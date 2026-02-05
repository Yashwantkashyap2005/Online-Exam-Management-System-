# Testing & Verification Guide

## ✅ System Health Check

### 1. Backend Server Status

```bash
# Check if server is running
curl http://localhost:5000/

# Expected response:
# "Online Examination Management System API is running..."
```

### 2. MongoDB Connection

Check the terminal where backend is running:
```
✅ Connected to MongoDB
```

If you see "Connected to MongoDB" - database connection is working!

### 3. Test Users

After running `npm run setup-db`, verify these accounts exist:

| Role | Email | Password |
|------|-------|----------|
| Admin | admin@exam.com | admin123 |
| Student | student@exam.com | student123 |
| Teacher | teacher@exam.com | teacher123 |

---

## 🧪 API Testing (Using Postman or curl)

### Test 1: Health Check
```bash
curl http://localhost:5000/
```
**Expected:** "Online Examination Management System API is running..."

### Test 2: Admin Login
```bash
curl -X POST http://localhost:5000/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "identifier": "admin@exam.com",
    "password": "admin123"
  }'
```
**Expected Response:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "...",
    "name": "Administrator",
    "email": "admin@exam.com",
    "role": "Admin"
  }
}
```

### Test 3: Student Login
```bash
curl -X POST http://localhost:5000/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "identifier": "student@exam.com",
    "password": "student123"
  }'
```

### Test 4: Teacher Login
```bash
curl -X POST http://localhost:5000/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "identifier": "teacher@exam.com",
    "password": "teacher123"
  }'
```

### Test 5: Invalid Login
```bash
curl -X POST http://localhost:5000/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "identifier": "invalid@exam.com",
    "password": "wrongpassword"
  }'
```
**Expected:** 400 error with "Invalid credentials" message

### Test 6: Get All Users (Admin only)
Save the token from admin login, then:
```bash
curl http://localhost:5000/users \
  -H "Authorization: Bearer YOUR_TOKEN_HERE"
```

### Test 7: Get All Exams
```bash
curl http://localhost:5000/exams \
  -H "Authorization: Bearer YOUR_TOKEN_HERE"
```

---

## 🌐 Frontend Testing

### Start Frontend Server
```bash
cd frontend
npm run dev
```

You should see:
```
VITE v7.3.1  ready in XXX ms
➜  Local:   http://localhost:5173/
```

### Test 1: Access Application
Open browser: `http://localhost:5173/`

You should see: **Login page**

### Test 2: Login as Admin
1. Enter: `admin@exam.com`
2. Enter Password: `admin123`
3. Click "Login"
4. Should redirect to: `/admin` (Admin Dashboard)

### Test 3: Login as Student
1. Go back to login
2. Enter: `student@exam.com`
3. Enter Password: `student123`
4. Click "Login"
5. Should redirect to: `/student` (Student Dashboard)

### Test 4: Login as Teacher
1. Go back to login
2. Enter: `teacher@exam.com`
3. Enter Password: `teacher123`
4. Click "Login"
5. Should redirect to: `/teacher` (Teacher Dashboard)

### Test 5: Sign Up New User
1. Click "Don't have an account?"
2. Fill in details:
   - Name: Test User
   - Email: testuser@example.com
   - Password: test123456
   - Roll No: 9999
   - Course: B.Tech
   - Semester: 6th
3. Click "Sign Up"
4. Should create account and login automatically

### Test 6: Profile Update
1. Login as student
2. Click Profile icon/menu
3. Update details
4. Changes should be saved

### Test 7: Logout
1. Click Logout button
2. Should redirect to login page
3. Token should be cleared from localStorage

---

## 🔍 Advanced Testing

### Check MongoDB Data

Use MongoDB Atlas Web Console:
1. Go to https://cloud.mongodb.com
2. Login with your credentials
3. Go to "Browse Collections"
4. Select database: `online-exam-system`
5. Collections to check:
   - `users` - Should have 3+ documents
   - `exams` - Exams created
   - `submissions` - Student submissions

### Check Browser Console (F12)
1. Open DevTools (F12)
2. Go to "Console" tab
3. Should NOT see red errors
4. Check "Network" tab for API calls

### Check Backend Console
Terminal where backend is running should show:
```
✅ Server is running on port 5000
✅ Connected to MongoDB
```

For each login, you should see:
```
Login successful for user: admin@exam.com
```

### Check localStorage
1. Open DevTools (F12)
2. Go to "Application" → "Local Storage"
3. Should contain:
   - `token` - JWT token
   - `user` - JSON user data

---

## 🚨 Common Issues & Solutions

### Issue: "Cannot connect to MongoDB"
**Solution:**
- Check `.env` file has correct connection string
- Verify MongoDB Atlas cluster is running
- Check IP whitelist includes your IP
- Ensure firewall isn't blocking connection

### Issue: "Invalid token" error
**Solution:**
- Clear localStorage: `localStorage.clear()`
- Login again
- Check token is being sent in requests

### Issue: Login page keeps reloading
**Solution:**
- Check browser console for errors (F12)
- Verify backend is running (`npm start`)
- Check API URL in `frontend/.env`
- Clear browser cache

### Issue: "CORS error"
**Solution:**
- Backend already has CORS enabled
- Check frontend is on localhost:5173
- Check backend is on localhost:5000

### Issue: "User not found" on login
**Solution:**
- Run `npm run setup-db` to create test users
- Check MongoDB has users collection
- Verify you're using correct email/password

### Issue: Database operations slow
**Solution:**
- Check internet connection (MongoDB Atlas is cloud)
- Check cluster resources not maxed out
- Verify no expensive queries running

---

## ✨ Full Test Workflow

### Quick Test (5 minutes)

```bash
# Terminal 1: Backend
cd backend
npm start
# Wait for "Connected to MongoDB"

# Terminal 2: Setup Users
cd backend
node scripts/setupTestUsers.js
# Wait for "Test Users Setup Complete!"

# Terminal 3: Frontend
cd frontend
npm run dev
# Wait for Vite to start

# Browser: Open http://localhost:5173
# Try login with: admin@exam.com / admin123
```

### Comprehensive Test (15 minutes)

1. ✅ Test backend health check (curl)
2. ✅ Test admin login (curl)
3. ✅ Test student login (curl)
4. ✅ Test invalid login (curl)
5. ✅ Start frontend
6. ✅ Test login in browser
7. ✅ Test sign up in browser
8. ✅ Test dashboard features
9. ✅ Check MongoDB data
10. ✅ Check browser console errors

---

## 📊 Expected Results Summary

### Backend Tests
- ✅ Health check returns "API is running"
- ✅ MongoDB connection established
- ✅ Admin login returns token
- ✅ Invalid login returns 400 error
- ✅ User endpoints require authentication

### Frontend Tests
- ✅ Login page loads correctly
- ✅ Login with valid credentials redirects to dashboard
- ✅ Login with invalid credentials shows error
- ✅ Sign up creates new account
- ✅ Logout clears token and redirects
- ✅ No console errors

### Database Tests
- ✅ MongoDB Atlas connected
- ✅ Users collection has 3+ documents
- ✅ Data is persistent (not lost on restart)

---

## 🎯 Quick Commands Reference

```bash
# Backend
npm start                # Start server
npm run setup-db        # Create test users
npm run create-admin    # Create admin
npm run create-student  # Create student

# Frontend
npm run dev             # Start dev server
npm run build          # Build for production
npm run lint           # Check code quality

# Testing
curl http://localhost:5000/              # Health check
curl http://localhost:5000/auth/login -X POST  # Login test
```

---

## ⚙️ System Requirements Check

Before running tests, verify:

- ✅ Node.js v16+ installed (`node --version`)
- ✅ MongoDB Atlas cluster running
- ✅ Internet connection (for MongoDB Atlas)
- ✅ Ports 5000 and 5173 available
- ✅ `.env` file properly configured
- ✅ All dependencies installed (`npm install`)

---

**Everything should be working correctly now! 🚀**

If you face any issues, check the "Common Issues & Solutions" section above.
