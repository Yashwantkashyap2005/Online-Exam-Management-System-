# Quick Reference & Cheat Sheet

## 🚀 START PROJECT (सबसे आसान तरीका)

### Option 1: Manual (3 Terminals)

**Terminal 1:**
```bash
cd backend
npm start
```

**Terminal 2:**
```bash
cd backend
npm run setup-db
```

**Terminal 3:**
```bash
cd frontend
npm run dev
```

**Browser:** `http://localhost:5173`

---

## 👤 Login करने के लिए

| उदाहरण | Email | Password |
|--------|-------|----------|
| Admin | admin@exam.com | admin123 |
| Student | student@exam.com | student123 |
| Teacher | teacher@exam.com | teacher123 |

---

## 🔍 कैसे Check करें सब काम कर रहा है?

### Step 1: Backend Check
Terminal में देखो:
```
✅ Server is running on port 5000
✅ Connected to MongoDB
```

### Step 2: Database Check  
Terminal में रन करो:
```bash
npm run setup-db
```
Output में देखो:
```
✅ Admin created
✅ Student created
✅ Teacher created
```

### Step 3: Frontend Check
Browser में खोलो: `http://localhost:5173`

नज़र आना चाहिए: **Login page**

### Step 4: Login Test
- Email: `admin@exam.com`
- Password: `admin123`
- Click Login

Redirect होना चाहिए: **Admin Dashboard**

---

## 🎯 Expected Results

### ✅ सब कुछ सही है अगर:

1. **Backend Terminal**
   - "Server is running on port 5000" ✅
   - "Connected to MongoDB" ✅

2. **Frontend Browser**
   - Login page load होता है ✅
   - Login form काम करता है ✅
   - Dashboard open होता है ✅

3. **Database**
   - Users create होते हैं ✅
   - Login data verify होता है ✅

---

## 🚨 समस्या & समाधान

### Problem 1: "Cannot find module"
**समाधान:**
```bash
cd backend
npm install
```

### Problem 2: "Cannot connect to MongoDB"
**समाधान:**
- Check `.env` file में MONGODB_URI सही है
- MongoDB Atlas cluster चल रहा है
- Internet connection है

### Problem 3: "Login page नहीं खुल रहा"
**समाधान:**
```bash
# पहले backend start करो
cd backend && npm start

# फिर frontend start करो (नए terminal में)
cd frontend && npm run dev
```

### Problem 4: "Test users नहीं बन रहे"
**समाधान:**
```bash
cd backend
node scripts/setupTestUsers.js
```

---

## 📊 Files & Folders की महत्ता

```
Online Examination Management System/
├── backend/               ← Server Code
│   ├── models/           ← Database schemas
│   ├── routes/           ← API endpoints
│   ├── scripts/          ← Helper scripts
│   ├── .env              ← Database credentials (शीर्ष गोपनीय!)
│   └── server.js         ← Main server
│
├── frontend/             ← Website Code
│   ├── src/
│   │   ├── pages/       ← Login, Dashboard, etc
│   │   ├── components/  ← Reusable components
│   │   └── services/    ← API calls
│   └── .env.example     ← API URL config
│
├── TESTING_GUIDE.md     ← विस्तृत testing guide
├── MONGODB_ATLAS_SETUP.md ← Database setup guide
└── README.md            ← Project info
```

---

## 💾 Important Commands

### Backend Commands
```bash
cd backend

# Server start करो
npm start

# Development mode (auto-reload)
npm run dev

# Test users setup
npm run setup-db

# Individual user create
npm run create-admin
npm run create-student
npm run create-teacher
```

### Frontend Commands
```bash
cd frontend

# Development server start
npm run dev

# Production build
npm run build

# Code check
npm run lint

# Built project preview
npm run preview
```

---

## 🔐 Configuration (.env)

### Backend (.env)
```
PORT=5000
MONGODB_URI=mongodb+srv://examadmin:examadmin123@cluster0.zztxw1x.mongodb.net/online-exam-system?retryWrites=true&w=majority
JWT_SECRET=supersecretkey123
NODE_ENV=development
```

### Frontend (.env) 
```
VITE_API_URL=http://localhost:5000
```

---

## 📱 Ports & URLs

| Service | Port | URL |
|---------|------|-----|
| Backend API | 5000 | http://localhost:5000 |
| Frontend | 5173 | http://localhost:5173 |
| MongoDB | 27017 | MongoDB Atlas Cloud |

---

## 🧪 Testing एक नज़र में

| Test | कहाँ | कैसे |
|------|------|------|
| Backend Health | Terminal | `npm start` देखो |
| Database | MongoDB Atlas | Login करके collections देखो |
| Login | Browser | http://localhost:5173 खोलो |
| API | curl/Postman | `curl http://localhost:5000/` |

---

## 💡 Pro Tips

1. **Different users login करने के लिए:**
   - Logout करो
   - Different email से login करो
   - Automatic redirect होगा

2. **New user sign up करने के लिए:**
   - "Sign Up" पर click करो
   - Details भरो
   - Signup करो
   - Automatically logged in हो जाओगे

3. **Backend में changes करने के लिए:**
   - File edit करो
   - `npm run dev` use करो (auto-reload)
   - Browser में F5 दबाओ

4. **MongoDB data देखने के लिए:**
   - Atlas website खोलो
   - Browse Collections click करो
   - Collections देखो

---

## 🎓 Learning Resources

- **REST API**: `/backend/routes/*` देखो
- **Database Schema**: `/backend/models/*` देखो
- **Frontend Pages**: `/frontend/src/pages/*` देखो
- **Components**: `/frontend/src/components/*` देखो

---

## ✅ System Health Checklist

- [ ] Backend running (port 5000) ✅
- [ ] Frontend running (port 5173) ✅
- [ ] MongoDB Atlas connected ✅
- [ ] Test users created ✅
- [ ] Login working ✅
- [ ] Dashboard loading ✅
- [ ] API endpoints working ✅
- [ ] Database data persisting ✅

---

## 🆘 Emergency Fixes

**Everything broken?**
```bash
# Kill everything
# (Close all terminals)

# Fresh start
cd backend && npm install
cd ../frontend && npm install

# Run again
# Terminal 1: cd backend && npm start
# Terminal 2: cd backend && npm run setup-db
# Terminal 3: cd frontend && npm run dev
```

---

## 📞 Support Docs

- DEVELOPMENT.md - Developer guide
- TESTING_GUIDE.md - Testing procedures
- MONGODB_ATLAS_SETUP.md - Database setup
- README.md - Project overview

---

**याद रखो:** Backend पहले, फिर Frontend! 🚀

