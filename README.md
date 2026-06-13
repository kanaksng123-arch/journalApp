# Journal App 📓

A production-grade backend REST API application built with Spring Boot, featuring JWT authentication, Google OAuth2 login, real-time weather integration, sentiment analysis, and asynchronous email notifications.

## 🔗 Links
- **Live Demo:** https://journalapp-production-caa3.up.railway.app/journal/swagger-ui/index.html
- **GitHub:** https://github.com/kanaksng123-arch/journalApp

## 🛠️ Tech Stack
- **Framework:** Spring Boot 2.7.16
- **Database:** MongoDB Atlas
- **Cache:** Redis Cloud
- **Security:** Spring Security + JWT + Google OAuth2
- **Messaging:** Apache Kafka
- **Email:** Gmail SMTP
- **API Docs:** Swagger / OpenAPI
- **Build Tool:** Maven
- **Deployment:** Railway

## ✨ Features
- User registration and login with JWT authentication
- Google OAuth2 login support
- Create, read, update, delete journal entries
- Real-time weather data shown on user greeting (Weatherstack API)
- Redis caching for weather responses (300s TTL)
- Weekly sentiment analysis of journal entries (HAPPY/SAD/ANGRY/ANXIOUS)
- Automated Sunday email reports via Kafka + Gmail SMTP
- Role-based authorization (USER / ADMIN)
- Swagger UI for interactive API testing
- All secrets managed via environment variables

## 🏗️ Architecture
Client → Spring Security (JWT Filter) → Controllers → Services → MongoDB Atlas

↓

Redis Cache

↓

Weatherstack API

↓

Kafka → Email Service

## 🚀 API Endpoints
### Public
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /public/health-check | Health check |
| POST | /public/signup | Register new user |
| POST | /public/login | Login and get JWT token |

### Journal (Requires Authentication)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /journal | Get all journal entries |
| POST | /journal | Create new entry |
| GET | /journal/id/{id} | Get entry by ID |
| PUT | /journal/id/{id} | Update entry |
| DELETE | /journal/id/{id} | Delete entry |

### User (Requires Authentication)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /user | Get greeting + weather |
| PUT | /user | Update profile |
| DELETE | /user | Delete account |

### Admin (Requires ADMIN Role)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /admin/all-users | Get all users |
| POST | /admin/create-admin-user | Create admin |
| GET | /admin/clear-app-cache | Refresh cache |

## 🔐 Authentication
1. Sign up via POST /public/signup
2. Login via POST /public/login → get JWT token
3. Add token to Swagger Authorize button as: `Bearer <token>`
4. All protected endpoints now accessible

## ⚙️ Environment Variables
MONGODB_URI

REDIS_URI

GOOGLE_CLIENT_ID

GOOGLE_CLIENT_SECRET

WEATHER_API_KEY

JAVA_EMAIL

JAVA_EMAIL_PASSWORD

JWT_SECRET

## 👨‍💻 Developer
**Kanak** — B.Tech EEE Student, BPIT Delhi  
Self-learning Java backend development
