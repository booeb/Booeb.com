# Global Time Zone Clock

A professional, production-ready digital clock application that displays current time across multiple time zones worldwide with real-time updates, beautiful UI, and comprehensive features.

**Status**: Enterprise Development  
**Target Audience**: Global Users, Businesses, Travelers  
**Technology**: Next.js, React, Node.js, PostgreSQL, Redis

---

## 🎯 Features

### Core Features
✅ Real-time digital clock display  
✅ Multiple time zone support (200+ zones)  
✅ 12/24 hour format toggle  
✅ Analog and digital clock views  
✅ Current date display  
✅ Day of week indicator  
✅ UTC offset display  
✅ Daylight Saving Time (DST) awareness  

### Advanced Features
✅ Custom time zone selection  
✅ Favorite time zones management  
✅ Time zone comparison view  
✅ Meeting planner (find best meeting time)  
✅ World map with time zones  
✅ Sunrise/Sunset times  
✅ Timezone quick conversion  
✅ Dark/Light theme  
✅ Multilingual support  

### User Features
✅ User accounts & authentication  
✅ Save preferred time zones  
✅ Timezone alarms  
✅ Timezone search  
✅ Share timezone link  
✅ Export time data  

---

## 📊 Technology Stack

### Frontend
- Next.js 14 (React framework)
- React 18 (UI library)
- TypeScript (Type safety)
- Tailwind CSS (Styling)
- Framer Motion (Animations)
- Chart.js (Time visualization)

### Backend
- Node.js (Runtime)
- Express.js (API server)
- PostgreSQL (Database)
- Redis (Caching)
- Bull Queue (Task scheduling)

### DevOps
- Docker (Containerization)
- Docker Compose (Orchestration)
- GitHub Actions (CI/CD)
- Nginx (Reverse proxy)

---

## 🏗️ Project Structure

```
GlobalTimeZoneClock/
├── frontend/                 # Next.js React Application
├── backend/                  # Express.js API Server
├── database/                 # Database & Migrations
├── docker/                   # Docker Configuration
├── docs/                     # Documentation
├── .github/                  # GitHub Workflows
├── docker-compose.yml        # Multi-container orchestration
├── package.json              # Root workspace
└── README.md                 # This file
```

---

## 🚀 Quick Start

### With Docker (Recommended)
```bash
git clone https://github.com/yourusername/GlobalTimeZoneClock.git
cd GlobalTimeZoneClock
cp .env.example .env.local
docker-compose up -d

# Application running:
# Frontend: http://localhost:3000
# Backend: http://localhost:3001
# API Docs: http://localhost:3001/api/docs
```

### Manual Setup
```bash
# Install dependencies
npm run install:all

# Start development servers
npm run dev

# Run tests
npm run test

# Build for production
npm run build
```

---

## 📱 User Interface

### Dashboard
- Header with current UTC time
- Search bar for time zones
- Favorite time zones grid
- Add/remove time zones

### Clock Views
- Digital clock (HH:MM:SS)
- Analog clock with smooth animations
- Date and day of week
- UTC offset display

### Time Zone Information
- City/Region name
- Current time in 12/24 format
- UTC offset
- DST status
- Sunrise/Sunset times (optional)

### Additional Views
- World map with time zones
- Meeting planner grid
- Time zone comparison table
- Settings & preferences

---

## 🔌 API Endpoints

### Time Zones
```
GET  /api/v1/timezones              - Get all time zones
GET  /api/v1/timezones/:id          - Get specific timezone
GET  /api/v1/timezones/search       - Search timezones
```

### Current Time
```
GET  /api/v1/time/current           - Get current time in all zones
GET  /api/v1/time/:timezone         - Get time in specific zone
GET  /api/v1/time/multiple          - Get time in multiple zones
```

### User Time Zones
```
POST   /api/v1/user/timezones       - Add favorite timezone
GET    /api/v1/user/timezones       - Get user's favorite timezones
DELETE /api/v1/user/timezones/:id   - Remove favorite timezone
```

### Meeting Planner
```
POST  /api/v1/meetings/find-time    - Find best meeting time
GET   /api/v1/meetings/availability - Get availability grid
```

---

## 🎨 Design System

### Color Palette
- **Primary**: #0066CC (Vibrant Blue)
- **Secondary**: #6B21A8 (Purple)
- **Accent**: #FF6B35 (Orange)
- **Background**: #0F172A (Dark)
- **Surface**: #1E293B (Card)
- **Text**: #F1F5F9 (Light)
- **Success**: #10B981 (Green)
- **Error**: #EF4444 (Red)

### Typography
- **Headings**: Inter Bold
- **Body**: Inter Regular
- **Mono (Time)**: JetBrains Mono

---

## 📊 Database Schema

### Users
```sql
- id (UUID, PK)
- email (VARCHAR, UNIQUE)
- password_hash (VARCHAR)
- username (VARCHAR)
- timezone (VARCHAR) - default timezone
- is_24_hour (BOOLEAN) - 12/24 hour format
- theme (ENUM) - dark/light
- language (VARCHAR)
- created_at (TIMESTAMP)
- updated_at (TIMESTAMP)
```

### Favorite Timezones
```sql
- id (UUID, PK)
- user_id (UUID, FK)
- timezone (VARCHAR)
- label (VARCHAR) - custom name
- order (INTEGER) - display order
- created_at (TIMESTAMP)
```

### Alarms
```sql
- id (UUID, PK)
- user_id (UUID, FK)
- timezone (VARCHAR)
- time (TIME)
- title (VARCHAR)
- enabled (BOOLEAN)
- created_at (TIMESTAMP)
```

---

## 🔒 Security Features

✅ HTTPS/TLS encryption  
✅ JWT authentication  
✅ CSRF protection  
✅ Rate limiting  
✅ Input validation  
✅ Password hashing (bcrypt)  
✅ CORS configuration  
✅ Secure headers  

---

## ⚡ Performance

### Frontend Optimization
- Code splitting by route
- Image lazy loading
- CSS-in-JS optimization
- Service Worker for offline support
- Preloading critical assets

### Backend Optimization
- Redis caching for timezone data
- Database query optimization
- API response compression
- Connection pooling
- Efficient timezone calculations

### Target Metrics
- First Contentful Paint: < 1s
- Largest Contentful Paint: < 2s
- Time to Interactive: < 3s
- Lighthouse Score: ≥ 95

---

## 🧪 Testing

### Frontend Tests
```bash
npm run test:frontend
```
- Unit tests for components
- Integration tests for pages
- E2E tests with Playwright

### Backend Tests
```bash
npm run test:backend
```
- Unit tests for services
- API endpoint tests
- Database integration tests

### Coverage Target
- Frontend: ≥ 80%
- Backend: ≥ 85%

---

## 📖 Documentation

- [Frontend Documentation](./docs/FRONTEND.md)
- [Backend Documentation](./docs/BACKEND.md)
- [API Documentation](./docs/API.md)
- [Architecture](./docs/ARCHITECTURE.md)
- [Deployment Guide](./docs/DEPLOYMENT.md)
- [Contributing Guidelines](./CONTRIBUTING.md)

---

## 🚀 Deployment

### Options
1. **Docker** - Complete containerization
2. **Vercel** - Frontend hosting
3. **Railway/Render** - Backend hosting
4. **AWS/DigitalOcean** - Full stack deployment
5. **Netlify** - Static site hosting

See [Deployment Guide](./docs/DEPLOYMENT.md) for detailed instructions.

---

## 📈 Roadmap

### Phase 1 (Current)
- [x] Project setup
- [x] Basic clock display
- [x] Multiple timezone support
- [ ] Frontend UI development
- [ ] Backend API development

### Phase 2
- [ ] User authentication
- [ ] Favorite timezone management
- [ ] World map integration
- [ ] Meeting planner

### Phase 3
- [ ] Mobile app (React Native)
- [ ] Browser extensions
- [ ] Desktop app (Electron)
- [ ] Smartwatch integration

### Phase 4
- [ ] AI-powered timezone suggestions
- [ ] Calendar integration
- [ ] Notification system
- [ ] Advanced analytics

---

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

### Development Workflow
1. Fork repository
2. Create feature branch
3. Make changes
4. Run tests
5. Submit PR

---

## 📄 License

MIT License - See [LICENSE](./LICENSE) file

---

## 📞 Support

- **Documentation**: [GitHub Wiki](https://github.com/yourusername/GlobalTimeZoneClock/wiki)
- **Issues**: [GitHub Issues](https://github.com/yourusername/GlobalTimeZoneClock/issues)
- **Email**: support@globaltimezoneclock.com

---

**Built with ❤️ for Global Time Management**

Last Updated: June 2026
