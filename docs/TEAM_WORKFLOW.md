# Team Workflow Guide

Complete guide for team collaboration, setup, and development workflow.

## 📋 Table of Contents
1. [Initial Setup](#initial-setup)
2. [Daily Workflow](#daily-workflow)
3. [Making Changes](#making-changes)
4. [Pull Requests](#pull-requests)
5. [Troubleshooting](#troubleshooting)

---

## Initial Setup

### Step 1: Clone Repository
```powershell
git clone https://github.com/Yashwantkashyap2005/Online-Exam-Management-System-.git
cd Online-Exam-Management-System-
```

### Step 2: Install Dependencies
```powershell
npm install
# This installs dependencies for both backend and frontend (if workspace configured)

# Or install separately:
cd backend && npm install
cd ../frontend && npm install
```

### Step 3: Configure Environment Variables

**Backend Setup:**
```powershell
cd backend
```
- Copy `.env.example` to `.env`
- Replace placeholder values with your actual credentials:
  ```
  MONGODB_URI=your_mongodb_atlas_connection_string
  JWT_SECRET=your_secret_key_min_32_chars
  PORT=5000
  NODE_ENV=development
  ```

**Frontend Setup:**
```powershell
cd ../frontend
```
- Create `.env` file:
  ```
  VITE_API_URL=http://localhost:5000
  ```

### Step 4: Configure Git (First Time Only)
```powershell
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

### Step 5: Start Development Servers

**Terminal 1 - Backend:**
```powershell
cd backend
npm run dev
# Server runs on http://localhost:5000
```

**Terminal 2 - Frontend:**
```powershell
cd frontend
npm run dev
# App runs on http://localhost:5173
```

### Step 6: Test Login
- Open http://localhost:5173
- Login with test credentials:
  - **Admin**: admin@exam.com / admin123
  - **Student**: student@exam.com / student123
  - **Teacher**: teacher@exam.com / teacher123

---

## Daily Workflow

### Start of Day
1. **Pull latest changes:**
   ```powershell
   git pull origin main
   ```
2. **Install new dependencies (if any):**
   ```powershell
   npm install
   ```
3. **Start development servers** (as shown in Step 5 above)

### End of Day
1. **Commit your work:**
   ```powershell
   git add .
   git commit -m "Your descriptive message"
   ```
2. **Push to GitHub:**
   ```powershell
   git push origin your-feature-branch
   ```

---

## Making Changes

### Step 1: Create Feature Branch
```powershell
git checkout main
git pull origin main
git checkout -b feature/feature-name
# Examples: feature/add-login, feature/fix-exam-submit, feature/improve-ui
```

### Step 2: Make Your Changes
- Edit code in your preferred editor
- Keep changes focused on one feature
- Test your changes locally

### Step 3: Commit Changes
```powershell
git add .
git commit -m "Brief description of changes"
# Good commit messages:
# - "Add user authentication page"
# - "Fix MongoDB connection timeout"
# - "Improve exam result display"
```

### Step 4: Push to GitHub
```powershell
git push origin feature/feature-name
```

---

## Pull Requests

### Creating a PR
1. Go to GitHub repository
2. Click "Pull requests" → "New pull request"
3. Select:
   - Base branch: `main`
   - Compare branch: Your `feature/branch-name`
4. Fill in:
   - **Title**: Clear, descriptive title
   - **Description**: What changes, why, what to test
5. Click "Create pull request"

### PR Description Template
```markdown
## Description
Brief description of the changes made.

## Related Issues
Closes #123

## Changes
- Change 1
- Change 2
- Change 3

## How to Test
1. Step 1
2. Step 2
3. Step 3

## Screenshots (if applicable)
[Add screenshots here]
```

### PR Checklist (Before Submit)
- [ ] Code follows project style guide
- [ ] Changes tested locally
- [ ] No console errors
- [ ] Dependencies updated in package.json
- [ ] Commit messages are descriptive
- [ ] Related documentation updated

### After PR Review
- Address review comments
- Make additional commits with fixes
- Push again (PR updates automatically)
- Request review when ready

---

## Handling Merge Conflicts

### If Conflict Occurs
```powershell
# Your branch has conflicts with main
git pull origin main

# Resolve conflicts in editor
# Files will show:
# <<<<<<< HEAD (your changes)
# Your code
# =======
# Their code
# >>>>>>> branch-name

# After fixing, stage and commit:
git add .
git commit -m "Resolve merge conflicts"
git push origin your-branch
```

---

## Common Tasks

### Update Your Local main
```powershell
git checkout main
git pull origin main
```

### View Current Branch
```powershell
git branch
# Current branch has * before it
```

### List All Remote Branches
```powershell
git branch -r
```

### Delete Local Branch
```powershell
git branch -d feature/finished-feature
```

### Switch Branch
```powershell
git checkout another-branch
```

### See Changed Files
```powershell
git status
```

### See Commit History
```powershell
git log --oneline
# Shows last 10 commits
```

---

## Code Standards

### File Organization
- Backend: `backend/models`, `backend/routes`, `backend/middleware`
- Frontend: `frontend/src/components`, `frontend/src/pages`, `frontend/src/services`

### Naming Conventions
- Files: kebab-case (`user-profile.jsx`, `auth.js`)
- Functions: camelCase (`handleUserLogin()`)
- Constants: UPPERCASE_SNAKE_CASE (`MONGODB_URI`)
- CSS Classes: kebab-case (`.user-card`)

### Code Quality
- Run `npm audit` before committing
- Check for console errors
- Test on both desktop and mobile (if applicable)
- Write meaningful variable/function names

---

## Troubleshooting

### Git Issues

**"Can't push changes"**
```powershell
# Pull latest changes first
git pull origin your-branch
# Resolve any conflicts
git push origin your-branch
```

**"Accidentally committed to main"**
```powershell
git reset HEAD~1        # Undo last commit
git checkout -b feature/your-feature  # Create new branch
git commit -m "Your message"
git push origin feature/your-feature
```

**"Need to undo changes"**
```powershell
# Undo all changes since last commit
git checkout .

# Or for specific file
git checkout -- filename.js
```

### Node/NPM Issues

**"npm install fails"**
```powershell
# Clear npm cache
npm cache clean --force
# Remove node_modules
rm -r node_modules
# Reinstall
npm install
```

**"Port already in use"**
```powershell
# Kill process on port 5000 (backend)
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# Or change PORT in .env
PORT=5001
```

**"Dependencies not updating"**
```powershell
npm update
npm audit fix
```

### Development Issues

**"Frontend can't connect to backend"**
- Check backend server is running on http://localhost:5000
- Verify VITE_API_URL in frontend/.env
- Check CORS settings in backend/server.js

**"MongoDB connection error"**
- Verify MONGODB_URI in backend/.env
- Check MongoDB Atlas IP whitelist
- Confirm database name is correct

**"Authentication fails after login"**
- Check JWT_SECRET in backend/.env
- Clear browser localStorage
- Check token expiration settings

---

## Best Practices

### ✅ DO
- Commit frequently with meaningful messages
- Pull before starting work
- Create branches for each feature
- Test before pushing
- Keep commits focused and atomic
- Write clear PR descriptions
- Document complex code

### ❌ DON'T
- Push directly to main branch
- Make large commits mixing multiple features
- Ignore merge conflicts
- Commit sensitive data (.env files)
- Push broken code
- Force push (`git push --force`) unless absolutely necessary
- Commit node_modules or build files

---

## Quick Reference Commands

```powershell
# Setup
git clone [repo-url]
npm install

# Daily
git pull origin main
npm run dev

# Development
git checkout -b feature/name
git add .
git commit -m "message"
git push origin feature/name

# Cleanup
git checkout main
git pull origin main
git branch -d old-branch

# Undo
git reset HEAD~1
git checkout .
```

---

## Need Help?

1. **Check existing issues**: GitHub Issues tab
2. **Create new issue**: Provide clear description and error logs
3. **Ask in team**: Check with team members first
4. **Documentation**: Review [DEVELOPMENT.md](DEVELOPMENT.md) and [SECURITY.md](SECURITY.md)

---

## Version
- Last Updated: February 2026
- Team Workflow v1.0
