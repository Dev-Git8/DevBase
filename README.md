# 🚀 DEVBASE

**Backend-as-a-Service Platform for Developers**

Build scalable backends in minutes — not days.

---

## 🧠 Introduction

BackForge is a developer-first Backend-as-a-Service (BaaS) platform designed to eliminate repetitive backend development tasks. It provides a complete backend infrastructure including authentication, dynamic data APIs, API key management, rate limiting, and request debugging tools.

Instead of building backend systems from scratch for every project, developers can use BackForge to instantly provision and manage backend services, allowing them to focus on building product features rather than infrastructure.

---

## 🎯 Problem Statement

Modern applications require:

- **Authentication systems** - Secure user management and JWT tokens
- **Database management** - Schema creation and data persistence
- **API development** - Building RESTful endpoints for each project
- **Security & rate limiting** - Protecting against abuse and unauthorized access

These components are repeatedly built across projects, leading to **wasted time** and **inconsistent implementations**.

---

## 💡 Solution

BackForge abstracts these repetitive backend concerns into a single platform that:

✅ Generates APIs dynamically  
✅ Provides secure access via API keys  
✅ Handles authentication out of the box  
✅ Enables debugging with request logging & replay  

---

## ✨ Features

### 🔐 Authentication
- JWT-based authentication (Access & Refresh tokens)
- Secure password hashing with bcrypt
- Token refresh mechanisms

### 🏗️ Multi-Tenant Architecture
- Users can create multiple projects
- Each project is isolated and secure
- Project-level API keys and configurations

### 🔑 API Key Management
- Generate API keys per project
- Middleware-based validation
- Automatic API key rotation support

### 🗄️ Dynamic CRUD APIs
- Create collections dynamically
- Automatic REST API generation
- Schema-based validation

### 📜 Logging & Debugging
- Request logging system
- Replay requests for debugging
- Request inspection and analysis

### 🚦 Rate Limiting
- Redis-based rate limiting
- Configurable rate limits per API key
- Prevent API abuse

### 🧪 Validation
- Schema validation using Zod
- Request/response validation
- Type-safe operations

### 📊 Analytics (Basic)
- Track API usage
- Monitor requests and errors
- Usage statistics dashboard

---

## 🧱 Tech Stack

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **TypeScript** - Type safety

### Database
- **PostgreSQL** - Relational database
- **Prisma ORM** - Database abstraction layer

### Caching & Jobs
- **Redis** - In-memory cache and rate limiting
- **BullMQ** - Job queue system

### Validation & Security
- **Zod** - Schema validation
- **JWT** - JSON Web Tokens
- **bcrypt** - Password hashing

### DevOps & Tools
- **Docker** - Containerization
- **Swagger (OpenAPI)** - API documentation
- **Postman** - API testing

---

## 🧩 Architecture Overview

```
    Client
      ↓
   API Gateway
      ↓
  Middleware Layer
      ↓
   Services
      ↓
   Database
      
    (Parallel)
      ↓
  Logging System
      ↓
  Replay Engine
```

---

## ⚙️ How It Works

### 1️⃣ User Authentication
- User signs up and logs in
- Receives JWT token (access & refresh)
- Token used for subsequent requests

### 2️⃣ Project Creation
- User creates a project
- Project acts as an isolated backend environment
- Project gets unique credentials

### 3️⃣ API Key Generation
- Each project generates API keys
- Requests are authenticated via API keys
- Keys can be revoked or rotated

### 4️⃣ Dynamic Data Handling
- Users create collections (like database tables)
- CRUD APIs are automatically available
- No need to write endpoint code

### 5️⃣ Request Processing Flow

```
Request → Auth → API Key → Rate Limit → Validation → Controller → DB → Response
```

### 6️⃣ Logging & Replay
- Every request is stored with metadata
- Users can replay requests for debugging
- View request/response history

---

## 📡 API Reference

### 🔐 Authentication Endpoints
```
POST   /auth/signup          - Create new user account
POST   /auth/login           - Authenticate and receive tokens
POST   /auth/refresh         - Refresh access token
```

### 🏗️ Project Management
```
POST   /projects             - Create new project
GET    /projects             - List all user projects
GET    /projects/:id         - Get project details
DELETE /projects/:id         - Delete project
```

### 🔑 API Key Management
```
POST   /apikeys              - Generate new API key
GET    /apikeys              - List all API keys
DELETE /apikeys/:id          - Revoke API key
```

### 🗄️ Dynamic Data APIs
```
POST   /data/:collection     - Create new record
GET    /data/:collection     - List all records
GET    /data/:collection/:id - Get specific record
PUT    /data/:collection/:id - Update record
DELETE /data/:collection/:id - Delete record
```

### 📜 Logs & Replay
```
GET    /logs                 - Get request logs
GET    /logs/:id             - Get log details
POST   /logs/:id/replay      - Replay a request
```

---

## 🧪 Example Usage

### Request
```bash
POST /data/posts
Content-Type: application/json
Authorization: Bearer <api-key>

{
  "title": "BackForge Launch",
  "views": 100
}
```

### Response
```json
{
  "id": "abc123",
  "title": "BackForge Launch",
  "views": 100,
  "createdAt": "2024-04-07T10:30:00Z",
  "updatedAt": "2024-04-07T10:30:00Z"
}
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js (v16+)
- npm or yarn
- PostgreSQL
- Redis

### 1. Clone Repository
```bash
git clone https://github.com/Dev-Git8/DevBase.git
cd DevBase
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Set Environment Variables

Create a `.env` file in the root directory:

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/backforge

# JWT
JWT_SECRET=your_jwt_secret_key_here
JWT_EXPIRY=24h
REFRESH_TOKEN_SECRET=your_refresh_secret_key
REFRESH_TOKEN_EXPIRY=7d

# Redis
REDIS_URL=redis://localhost:6379

# Server
PORT=3000
NODE_ENV=development

# API
API_BASE_URL=http://localhost:3000
```

### 4. Run Database Migrations
```bash
npx prisma migrate dev
```

### 5. Seed Database (Optional)
```bash
npx prisma db seed
```

### 6. Start Development Server
```bash
npm run dev
```

The server will start on `http://localhost:3000`

---

## 🐳 Docker Setup

Build and run with Docker Compose:

```bash
docker-compose up --build
```

This will:
- Start PostgreSQL database
- Start Redis cache
- Start BackForge API server
- Apply database migrations

Access the API at `http://localhost:3000`

---

## 📚 Available Scripts

```bash
npm run dev          # Start development server with hot reload
npm run build        # Build TypeScript to JavaScript
npm run start        # Start production server
npm run prisma:generate  # Generate Prisma client
npm run prisma:migrate   # Run database migrations
npm test             # Run test suite
npm run lint         # Run ESLint
npm run format       # Format code with Prettier
```

---

## 📖 Documentation

- **API Documentation**: Visit `/api-docs` when server is running (Swagger UI)
- **Database Schema**: Check `prisma/schema.prisma`
- **Environment Configuration**: See `.env.example`

---

## 🔐 Security Best Practices

✅ Use HTTPS in production  
✅ Rotate API keys regularly  
✅ Use strong JWT secrets  
✅ Enable rate limiting for all endpoints  
✅ Implement CORS policies  
✅ Validate all user inputs  
✅ Use environment variables for secrets  
✅ Implement request logging and monitoring  

---

## 📈 Future Scope

🎯 Advanced analytics dashboard  
🎯 Visual schema builder UI  
🎯 Webhooks system for event-driven architecture  
🎯 Role-based access control (RBAC)  
🎯 Billing and subscription management  
🎯 Event-driven architecture with message queues  
🎯 Multi-region deployment support  
🎯 Advanced caching strategies  
🎯 GraphQL API support  
🎯 Microservices integration  

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 💬 Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing documentation
- Contact the development team

---

## 👨‍💻 Authors

**BackForge Development Team**

---

## 🙏 Acknowledgments

- Inspired by Firebase, Supabase, and similar BaaS platforms
- Built with ❤️ for developers

---

**Happy Building with BackForge! 🚀**
