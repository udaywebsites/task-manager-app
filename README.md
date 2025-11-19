# Task Manager - Full Stack Web Application

A scalable, secure task management web application with JWT authentication, built with React.js frontend and Node.js/Express backend.

## 🚀 Features

### Authentication & Security
- ✅ User registration and login with JWT authentication
- ✅ Password hashing using bcrypt
- ✅ Protected routes requiring authentication
- ✅ Token-based session management
- ✅ Secure API endpoints with middleware validation

### Dashboard Features
- ✅ Create, Read, Update, Delete (CRUD) operations on tasks
- ✅ Real-time task statistics (Total, Pending, In Progress, Completed)
- ✅ Advanced search functionality
- ✅ Filter by status and priority
- ✅ Sort tasks by multiple criteria
- ✅ Task categorization with tags
- ✅ Due date management

### User Profile Management
- ✅ View and update profile information
- ✅ Custom avatar support
- ✅ Bio and personal information
- ✅ Account creation date tracking

### UI/UX
- ✅ Responsive design with TailwindCSS
- ✅ Clean, modern interface
- ✅ Mobile-friendly layout
- ✅ Intuitive navigation
- ✅ Form validation (client & server-side)

## 📋 Tech Stack

### Frontend
- **React.js** - UI framework
- **React Router** - Client-side routing
- **TailwindCSS** - Styling and responsive design
- **Axios** - HTTP client
- **Context API** - State management

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **bcryptjs** - Password hashing
- **jsonwebtoken** - JWT authentication
- **express-validator** - Input validation

## 🛠️ Installation & Setup

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or Atlas)
- npm or yarn

### Backend Setup

1. Navigate to backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file (copy from `.env.example`):
```bash
cp .env.example .env
```

4. Configure environment variables in `.env`:
```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/taskmanager
JWT_SECRET=your_secure_jwt_secret_key_here
JWT_EXPIRE=7d
NODE_ENV=development
```

5. Start MongoDB (if running locally):
```bash
mongod
```

6. Start the backend server:
```bash
npm run dev
```

The backend will run on `http://localhost:5000`

### Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file (copy from `.env.example`):
```bash
cp .env.example .env
```

4. Configure environment variables in `.env`:
```env
REACT_APP_API_URL=http://localhost:5000/api
```

5. Start the development server:
```bash
npm start
```

The frontend will run on `http://localhost:3000`

## 📁 Project Structure

```
Prime_trade_assissgment/
├── backend/
│   ├── middleware/
│   │   └── auth.js              # JWT authentication middleware
│   ├── models/
│   │   ├── User.js              # User schema with password hashing
│   │   └── Task.js              # Task schema with validations
│   ├── routes/
│   │   ├── auth.js              # Authentication routes (login, register)
│   │   ├── user.js              # User profile routes
│   │   └── tasks.js             # Task CRUD routes
│   ├── utils/
│   │   └── generateToken.js     # JWT token generator
│   ├── server.js                # Express app entry point
│   ├── package.json
│   └── .env.example
│
└── frontend/
    ├── public/
    ├── src/
    │   ├── components/
    │   │   ├── Navbar.js        # Navigation component
    │   │   ├── PrivateRoute.js  # Protected route wrapper
    │   │   ├── TaskCard.js      # Task display component
    │   │   └── TaskModal.js     # Task create/edit modal
    │   ├── context/
    │   │   └── AuthContext.js   # Authentication context
    │   ├── pages/
    │   │   ├── Login.js         # Login page
    │   │   ├── Register.js      # Registration page
    │   │   ├── Dashboard.js     # Main dashboard
    │   │   └── Profile.js       # User profile page
    │   ├── utils/
    │   │   └── api.js           # Axios configuration
    │   ├── App.js               # Main app component
    │   ├── index.js             # Entry point
    │   └── index.css            # Global styles
    ├── package.json
    └── .env.example
```

## 🔐 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### User Profile
- `GET /api/user/profile` - Get user profile (Protected)
- `PUT /api/user/profile` - Update user profile (Protected)

### Tasks
- `GET /api/tasks` - Get all user tasks with filters (Protected)
- `GET /api/tasks/:id` - Get single task (Protected)
- `POST /api/tasks` - Create new task (Protected)
- `PUT /api/tasks/:id` - Update task (Protected)
- `DELETE /api/tasks/:id` - Delete task (Protected)

### Query Parameters for GET /api/tasks
- `status` - Filter by status (pending, in-progress, completed)
- `priority` - Filter by priority (low, medium, high)
- `search` - Search in title and description
- `sortBy` - Sort field (createdAt, updatedAt, title, priority)
- `order` - Sort order (asc, desc)

## 📝 API Documentation (Postman)

See `POSTMAN_COLLECTION.json` for complete API documentation and example requests.

Import the collection into Postman:
1. Open Postman
2. Click Import
3. Select `POSTMAN_COLLECTION.json`
4. All endpoints will be available with example requests

## 🔒 Security Features

1. **Password Security**
   - Passwords hashed using bcrypt (10 salt rounds)
   - Never stored in plain text
   - Not returned in API responses

2. **JWT Authentication**
   - Tokens expire after 7 days (configurable)
   - Secure token validation on protected routes
   - Automatic logout on token expiration

3. **Input Validation**
   - Server-side validation using express-validator
   - Client-side validation for better UX
   - SQL injection prevention (NoSQL)
   - XSS protection

4. **API Security**
   - CORS enabled
   - Rate limiting ready (can be added)
   - Error handling without exposing sensitive info

## 📈 Scalability Considerations

### Current Architecture
- **Modular Code Structure**: Separated concerns (routes, controllers, models)
- **RESTful API Design**: Stateless, cacheable endpoints
- **Database Indexing**: Optimized queries with MongoDB indexes
- **Environment Configuration**: Easy deployment across environments

### Production Scaling Strategy

#### Frontend Scaling
1. **CDN Integration**
   - Host static assets on CDN (CloudFront, Cloudflare)
   - Reduce server load and improve global performance

2. **Code Splitting**
   - Implement React lazy loading
   - Reduce initial bundle size
   - Faster page loads

3. **Caching Strategy**
   - Browser caching for static assets
   - Service workers for offline support
   - Redux/React Query for state management at scale

4. **Build Optimization**
   - Production builds with minification
   - Tree shaking for smaller bundles
   - Image optimization

#### Backend Scaling
1. **Horizontal Scaling**
   - Deploy multiple server instances
   - Load balancer (Nginx, AWS ALB)
   - Session management with Redis

2. **Database Optimization**
   - MongoDB sharding for large datasets
   - Read replicas for read-heavy operations
   - Connection pooling
   - Proper indexing strategy

3. **Caching Layer**
   - Redis for session storage
   - Cache frequently accessed data
   - Reduce database queries

4. **API Optimization**
   - Implement pagination for large datasets
   - Rate limiting to prevent abuse
   - Response compression (gzip)
   - API versioning for backward compatibility

5. **Microservices Architecture**
   - Separate auth service
   - Task management service
   - Notification service
   - Independent scaling of services

#### Infrastructure
1. **Containerization**
   - Docker for consistent environments
   - Kubernetes for orchestration
   - Auto-scaling based on load

2. **Cloud Deployment**
   - AWS: EC2, RDS, S3, CloudFront
   - Azure: App Service, Cosmos DB
   - Google Cloud: Compute Engine, Cloud SQL

3. **Monitoring & Logging**
   - Application monitoring (New Relic, DataDog)
   - Error tracking (Sentry)
   - Centralized logging (ELK stack)
   - Performance metrics (Prometheus, Grafana)

4. **CI/CD Pipeline**
   - Automated testing
   - Continuous deployment
   - Blue-green deployments
   - Rollback capabilities

## 🧪 Testing

### Backend Testing (Recommended)
```bash
cd backend
npm install --save-dev jest supertest
npm test
```

### Frontend Testing (Recommended)
```bash
cd frontend
npm test
```

## 🚀 Deployment

### Backend Deployment (Example: Heroku)
```bash
cd backend
heroku create your-app-name
heroku addons:create mongolab
git push heroku main
```

### Frontend Deployment (Example: Vercel)
```bash
cd frontend
npm run build
vercel deploy
```

### Docker Deployment
```bash
# Backend
cd backend
docker build -t task-manager-backend .
docker run -p 5000:5000 task-manager-backend

# Frontend
cd frontend
docker build -t task-manager-frontend .
docker run -p 3000:3000 task-manager-frontend
```

## 👤 Default Test User

For testing purposes, you can create a user through the registration page or use:
- Email: test@example.com
- Password: test123

## 📄 License

This project is open source and available under the MIT License.

## 👨‍💻 Author

Created as part of Prime Trade Assignment

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## ⭐ Show your support

Give a ⭐️ if you like this project!
