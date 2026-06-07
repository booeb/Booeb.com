# Backend - Global Time Zone Clock

Express.js backend API for the Global Time Zone Clock application.

## 📁 Project Structure

```
backend/
├── src/
│   ├── routes/
│   │   ├── index.ts
│   │   ├── timezone.routes.ts      # Timezone endpoints
│   │   ├── time.routes.ts          # Current time endpoints
│   │   ├── user.routes.ts          # User timezone preferences
│   │   ├── alarm.routes.ts         # Alarm management
│   │   └── auth.routes.ts          # Authentication
│   │
│   ├── controllers/
│   │   ├── timezoneController.ts
│   │   ├── timeController.ts
│   │   ├── userController.ts
│   │   ├── alarmController.ts
│   │   └── authController.ts
│   │
│   ├── services/
│   │   ├── timezoneService.ts
│   │   ├── timeService.ts
│   │   ├── userService.ts
│   │   └── alarmService.ts
│   │
│   ├── models/
│   │   ├── User.ts
│   │   ├── FavoriteTimezone.ts
│   │   ├── Alarm.ts
│   │   └── index.ts
│   │
│   ├── middleware/
│   │   ├── auth.ts
│   │   ├── errorHandler.ts
│   │   ├── logger.ts
│   │   └── validation.ts
│   │
│   ├── utils/
│   │   ├── jwt.ts
│   │   ├── logger.ts
│   │   ├── timezone.ts
│   │   └── constants.ts
│   │
│   ├── config/
│   │   ├── database.ts
│   │   ├── redis.ts
│   │   └── environment.ts
│   │
│   └── server.ts
│
├── .env.example
├── tsconfig.json
├── jest.config.js
├── package.json
└── Dockerfile
```

## 🔌 API Endpoints

### Timezones
```
GET  /api/v1/timezones              - Get all timezones
GET  /api/v1/timezones/search       - Search timezones
GET  /api/v1/timezones/:name        - Get timezone details
```

### Current Time
```
GET  /api/v1/time/current           - Get current time (all timezones)
GET  /api/v1/time/:timezone         - Get time in specific timezone
POST /api/v1/time/multiple          - Get time in multiple zones
```

### User Timezones
```
GET    /api/v1/user/timezones       - Get user's favorite timezones
POST   /api/v1/user/timezones       - Add favorite timezone
DELETE /api/v1/user/timezones/:id   - Remove favorite timezone
PUT    /api/v1/user/timezones/:id   - Update favorite timezone
```

### Alarms
```
GET    /api/v1/alarms               - Get user alarms
POST   /api/v1/alarms               - Create alarm
PUT    /api/v1/alarms/:id           - Update alarm
DELETE /api/v1/alarms/:id           - Delete alarm
```

### Authentication
```
POST /api/v1/auth/register          - User registration
POST /api/v1/auth/login             - User login
POST /api/v1/auth/logout            - User logout
POST /api/v1/auth/refresh           - Refresh token
```

## 🛠️ Installation

```bash
# Install dependencies
npm install

# Setup environment
cp .env.example .env

# Setup database
npm run db:setup

# Run development server
npm run dev
```

## 📦 Key Dependencies

- `express`: ^4.18.0
- `typescript`: ^5.0.0
- `pg`: ^8.10.0 (PostgreSQL)
- `redis`: ^4.6.0
- `jsonwebtoken`: ^9.0.0
- `zod`: ^3.21.0 (Validation)
- `winston`: ^3.8.0 (Logging)

## 🚀 Development

```bash
# Start dev server
npm run dev

# Run tests
npm run test

# Lint code
npm run lint

# Format code
npm run format

# Build
npm run build

# Start production
npm start
```

## 🔐 Security

- JWT authentication
- Password hashing
- Input validation
- Rate limiting
- CORS configuration
- Secure headers

## 📊 Database

### Users Table
- id (UUID)
- email (UNIQUE)
- password_hash
- username
- preferred_timezone
- is_24_hour
- theme
- created_at
- updated_at

### Favorite Timezones Table
- id (UUID)
- user_id (FK)
- timezone
- label
- order
- created_at

### Alarms Table
- id (UUID)
- user_id (FK)
- timezone
- time
- title
- enabled
- created_at

## 📖 API Documentation

Full API documentation available at `/api/docs` when server is running.

---

**Backend Ready for Development! ⚙️**
