# Quick Start Guide

## Prerequisites
- Node.js v14+ installed
- MongoDB installed and running (or MongoDB Atlas account)
- Git installed

## Installation Steps

### 1. Clone or Download the Project
```bash
cd c:\Users\udayk\Downloads\Prime_trade_assissgment
```

### 2. Backend Setup

Open a new terminal:

```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install

# Create .env file from example
copy .env.example .env

# Edit .env file with your configuration
# Minimum required:
# - MONGODB_URI (use your MongoDB connection string)
# - JWT_SECRET (use a secure random string)
```

**For MongoDB:**
- **Local MongoDB**: Use `mongodb://localhost:27017/taskmanager`
- **MongoDB Atlas**: Get connection string from Atlas dashboard

```bash
# Start the backend server
npm run dev
```

You should see:
```
✅ MongoDB Connected Successfully
🚀 Server running on port 5000
```

### 3. Frontend Setup

Open a **new terminal** (keep backend running):

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Create .env file from example
copy .env.example .env

# Start the development server
npm start
```

The browser should automatically open to `http://localhost:3000`

## 🎉 Success!

You should now see:
- **Backend**: Running on `http://localhost:5000`
- **Frontend**: Running on `http://localhost:3000`

## First Steps

1. **Register a new account** at `http://localhost:3000/register`
2. **Login** with your credentials
3. **Create your first task** from the dashboard
4. Explore features: search, filter, update profile

## Testing the API

Import `POSTMAN_COLLECTION.json` into Postman to test all API endpoints.

## Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running: `mongod`
- Check MONGODB_URI in backend/.env
- For Atlas, whitelist your IP address

### Port Already in Use
- Backend (5000): Change PORT in .env
- Frontend (3000): React will offer to use a different port

### Dependencies Installation Failed
```bash
# Clear cache and reinstall
npm cache clean --force
rm -rf node_modules package-lock.json
npm install
```

## Next Steps

- Read `README.md` for detailed documentation
- Check `SCALING_STRATEGY.md` for production deployment
- Import `POSTMAN_COLLECTION.json` for API testing

## Support

For issues, please check the full documentation in README.md
