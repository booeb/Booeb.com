# Production Deployment Guide

## 📋 Pre-Deployment Checklist

- [ ] All tests passing
- [ ] Code reviewed and approved
- [ ] Environment variables configured
- [ ] Database migrations prepared
- [ ] SSL certificates obtained
- [ ] CDN configured
- [ ] Backups scheduled
- [ ] Monitoring setup
- [ ] Error tracking configured

## 🚀 Deployment Options

### Option 1: VPS Deployment (Recommended for Bangladesh)

#### Prerequisites
- Ubuntu 22.04 LTS Server
- 4+ GB RAM, 2+ CPU cores
- 50GB+ SSD storage
- Root or sudo access

#### Step 1: System Setup

```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y curl wget git build-essential

# Install Node.js 18
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs

# Install PostgreSQL
sudo apt install -y postgresql postgresql-contrib

# Install Redis
sudo apt install -y redis-server

# Install Nginx
sudo apt install -y nginx

# Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# Install Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

#### Step 2: Clone and Setup Application

```bash
# Create application directory
sudo mkdir -p /var/www/booeb.com
cd /var/www/booeb.com

# Clone repository
sudo git clone https://github.com/booeb/Booeb.com.git .

# Set permissions
sudo chown -R $USER:$USER /var/www/booeb.com

# Copy environment file
cp .env.example .env.production

# Edit environment variables
nano .env.production
```

#### Step 3: Database Setup

```bash
# Create PostgreSQL database
sudo -u postgres psql << EOF
CREATE DATABASE booeb_db;
CREATE USER booeb_user WITH ENCRYPTED PASSWORD 'secure_password';
ALTER ROLE booeb_user SET client_encoding TO 'utf8';
ALTER ROLE booeb_user SET default_transaction_isolation TO 'read committed';
ALTER ROLE booeb_user SET default_transaction_deferrable TO on;
ALTER ROLE booeb_user SET default_transaction_read_committed TO off;
GRANT ALL PRIVILEGES ON DATABASE booeb_db TO booeb_user;
EOF

# Run migrations
npm run db:migrate
npm run db:seed
```

#### Step 4: Build Application

```bash
# Install dependencies
npm run install:all

# Build applications
npm run build
```

#### Step 5: Configure Nginx

```bash
# Create Nginx config
sudo nano /etc/nginx/sites-available/booeb.com
```

```nginx
upstream backend {
    server 127.0.0.1:3001;
}

upstream frontend {
    server 127.0.0.1:3000;
}

server {
    listen 80;
    server_name booeb.com www.booeb.com;
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name booeb.com www.booeb.com;

    ssl_certificate /etc/letsencrypt/live/booeb.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/booeb.com/privkey.pem;

    client_max_body_size 20M;

    # Security headers
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-XSS-Protection "1; mode=block" always;

    # Gzip compression
    gzip on;
    gzip_types text/plain text/css application/json application/javascript;

    # Frontend
    location / {
        proxy_pass http://frontend;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    # API
    location /api/ {
        proxy_pass http://backend;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

```bash
# Enable site
sudo ln -s /etc/nginx/sites-available/booeb.com /etc/nginx/sites-enabled/

# Test configuration
sudo nginx -t

# Restart Nginx
sudo systemctl restart nginx
```

#### Step 6: SSL Certificate (Let's Encrypt)

```bash
# Install Certbot
sudo apt install -y certbot python3-certbot-nginx

# Generate certificate
sudo certbot certonly --nginx -d booeb.com -d www.booeb.com

# Setup auto-renewal
sudo systemctl enable certbot.timer
sudo systemctl start certbot.timer
```

#### Step 7: Process Management with PM2

```bash
# Install PM2 globally
sudo npm install -g pm2

# Create PM2 ecosystem file
cat > ecosystem.config.js << 'EOF'
module.exports = {
  apps: [
    {
      name: 'booeb-backend',
      script: 'dist/server.js',
      cwd: '/var/www/booeb.com/backend',
      instances: 'max',
      exec_mode: 'cluster',
      env: {
        NODE_ENV: 'production'
      }
    },
    {
      name: 'booeb-frontend',
      script: 'npm',
      args: 'start',
      cwd: '/var/www/booeb.com/frontend',
      instances: 1,
      exec_mode: 'fork'
    }
  ]
};
EOF

# Start with PM2
pm2 start ecosystem.config.js

# Setup startup
pm2 startup
pm2 save

# Check status
pm2 status
```

#### Step 8: Monitoring and Logging

```bash
# Install Supervisor for process monitoring
sudo apt install -y supervisor

# View logs
pm2 logs

# Setup log rotation
sudo apt install -y logrotate
```

### Option 2: Docker Deployment

```bash
# Build images
docker-compose build

# Start services
docker-compose up -d

# Check status
docker-compose ps

# View logs
docker-compose logs -f
```

### Option 3: Cloud Platform Deployment

#### AWS ECS
```bash
# Build and push to ECR
aws ecr create-repository --repository-name booeb-frontend
aws ecr create-repository --repository-name booeb-backend

# Tag and push images
docker build -t booeb-frontend:latest ./frontend
docker tag booeb-frontend:latest <aws_account_id>.dkr.ecr.ap-southeast-1.amazonaws.com/booeb-frontend:latest
docker push <aws_account_id>.dkr.ecr.ap-southeast-1.amazonaws.com/booeb-frontend:latest
```

#### DigitalOcean App Platform
```bash
# Deploy using CLI
doctl apps create --spec app.yaml
```

#### Railway, Render, Vercel
- Frontend: Deploy to Vercel or Netlify
- Backend: Deploy to Railway, Render, or DigitalOcean

## 🔒 Security Hardening

```bash
# Enable firewall
sudo ufw enable
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Secure SSH
sudo sed -i 's/#PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
sudo systemctl restart sshd

# Regular backups
sudo crontab -e
# Add: 0 2 * * * /usr/local/bin/backup.sh
```

## 📊 Monitoring Setup

```bash
# Install Prometheus
sudo apt install -y prometheus

# Install Grafana
sudo apt install -y grafana-server

# Install Node Exporter
sudo apt install -y prometheus-node-exporter
```

## 🔄 CI/CD Integration

### GitHub Actions to Production

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to VPS
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.VPS_HOST }}
          username: ${{ secrets.VPS_USER }}
          key: ${{ secrets.VPS_KEY }}
          script: |
            cd /var/www/booeb.com
            git pull origin main
            npm run install:all
            npm run build
            pm2 restart ecosystem.config.js
```

## 🆘 Troubleshooting

### Service Won't Start
```bash
# Check logs
pm2 logs booeb-backend
pm2 logs booeb-frontend

# Restart
pm2 restart all
```

### Database Connection Issues
```bash
# Test connection
psql -h localhost -U booeb_user -d booeb_db -c "SELECT 1"

# Check PostgreSQL status
sudo systemctl status postgresql
```

### Nginx Configuration Error
```bash
# Test config
sudo nginx -t

# Check error log
sudo tail -f /var/log/nginx/error.log
```

---

**Deployment Completed Successfully! 🎉**
