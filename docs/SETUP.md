# Quick Setup Guide for Booeb.com

## 📋 Prerequisites

- Node.js 18+ ([Download](https://nodejs.org/))
- PostgreSQL 14+ ([Download](https://www.postgresql.org/download/))
- Redis 7+ ([Download](https://redis.io/download))
- Docker & Docker Compose (Optional, for containerized setup)
- Git ([Download](https://git-scm.com/))

## 🚀 Quick Start (Development)

### Option 1: With Docker (Recommended)

```bash
# Clone the repository
git clone https://github.com/booeb/Booeb.com.git
cd Booeb.com

# Copy environment file
cp .env.example .env.local

# Start all services with Docker
docker-compose up -d

# Setup database
docker-compose exec backend npm run db:setup

# Application is running:
# Frontend: http://localhost:3000
# Backend: http://localhost:3001
# Postgres: localhost:5432
# Redis: localhost:6379
```

### Option 2: Manual Setup (Local)

#### 1. Clone Repository
```bash
git clone https://github.com/booeb/Booeb.com.git
cd Booeb.com
```

#### 2. Setup Environment
```bash
cp .env.example .env.local

# Edit .env.local with your configuration
# Update database credentials, API keys, etc.
```

#### 3. Install Dependencies
```bash
npm run install:all
```

This installs dependencies for:
- Root workspace
- Frontend (Next.js)
- Backend (Express)

#### 4. Setup Database

```bash
# Create PostgreSQL database
createdb booeb_db -U booeb

# Run migrations
npm run db:migrate

# Seed sample data
npm run db:seed
```

#### 5. Start Development Servers
```bash
npm run dev
```

This runs:
- Frontend: http://localhost:3000
- Backend: http://localhost:3001

## 🛠️ Common Commands

### Development
```bash
npm run dev           # Start both frontend and backend
npm run dev:frontend  # Start frontend only
npm run dev:backend   # Start backend only
```

### Building
```bash
npm run build         # Build both applications
npm run build:frontend
npm run build:backend
```

### Testing
```bash
npm run test          # Run all tests
npm run test:frontend
npm run test:backend
```

### Code Quality
```bash
npm run lint          # Lint all code
npm run format        # Format code with Prettier
```

### Database
```bash
npm run db:setup      # Initial database setup
npm run db:migrate    # Run pending migrations
npm run db:seed       # Seed database with sample data
```

## 📁 Project Structure

```
Booeb.com/
├── frontend/          # Next.js React application
├── backend/           # Express.js API server
├── database/          # Database migrations & seeds
├── docker/            # Docker configuration
├── docs/              # Documentation
├── .github/           # GitHub workflows
└── package.json       # Root workspace configuration
```

## 🔗 Useful Links

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:3001
- **API Docs**: http://localhost:3001/api/docs
- **Database**: localhost:5432
- **Redis**: localhost:6379

## ⚙️ Environment Configuration

Key environment variables to configure:

```env
# Database
DB_HOST=localhost
DB_USER=booeb
DB_PASSWORD=your_password
DB_NAME=booeb_db

# JWT
JWT_SECRET=your_secret_key

# Payment Gateways
SSLCOMMERZ_STORE_ID=your_store_id
SSLCOMMERZ_STORE_PASSWORD=your_password
```

See `.env.example` for complete list.

## 🐛 Troubleshooting

### Port Already in Use
```bash
# Find process using port 3000/3001
lsof -i :3000
lsof -i :3001

# Kill process
kill -9 <PID>
```

### Database Connection Error
```bash
# Check if PostgreSQL is running
psql -U booeb -d booeb_db -c "SELECT 1"

# Reset database (WARNING: Loses all data)
npm run db:reset
```

### Node Modules Issues
```bash
# Clean install
rm -rf node_modules frontend/node_modules backend/node_modules
npm run install:all
```

### Docker Issues
```bash
# Stop all containers
docker-compose down

# Remove volumes (WARNING: Loses data)
docker-compose down -v

# Rebuild containers
docker-compose up --build
```

## 📚 Next Steps

1. **Review Documentation**
   - [API Documentation](./docs/API.md)
   - [Architecture](./docs/ARCHITECTURE.md)
   - [Deployment Guide](./docs/DEPLOYMENT.md)

2. **Explore Code**
   - Check `frontend/components` for React components
   - Check `backend/routes` for API endpoints
   - Review `database/schema` for database structure

3. **Start Development**
   - Create a feature branch: `git checkout -b feature/your-feature`
   - Make changes and test
   - Submit a pull request

4. **Join Community**
   - Read [Contributing Guidelines](./CONTRIBUTING.md)
   - Follow code standards
   - Get help from team

## 📞 Support

- **Documentation**: [GitHub Wiki](https://github.com/booeb/Booeb.com/wiki)
- **Issues**: [Report Issues](https://github.com/booeb/Booeb.com/issues)
- **Discussions**: [GitHub Discussions](https://github.com/booeb/Booeb.com/discussions)
- **Email**: dev@booeb.com

---

**Happy Coding! 🚀**
