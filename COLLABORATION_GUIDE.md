# GitHub Collaboration Guide - Share Project with Team Members

## 🤝 How to Share Project with Team Members

### Option 1: Add as Collaborator (Recommended)

This makes your team member a **direct collaborator** with push access.

#### Steps:

1. **Go to GitHub Repository Settings**
   - Open: https://github.com/Yashwantkashyap2005/Online-Exam-Management-System-
   - Click "Settings" tab (top right)
   - Click "Collaborators" (left sidebar)

2. **Add Team Member**
   - Click "Add people"
   - Enter team member's GitHub username
   - Click "Add"
   - Team member will get notification to accept

3. **Team Member Accepts**
   - Team member checks their GitHub notifications
   - Clicks accept on collaboration invitation
   - Now has access to clone and push

#### Team Member Setup:

```bash
# Clone repository
git clone https://github.com/Yashwantkashyap2005/Online-Exam-Management-System-.git
cd Online-Exam-Management-System

# Install dependencies
cd backend && npm install
cd ../frontend && npm install

# Configure git (one time)
git config user.name "Team Member Name"
git config user.email "team.member@email.com"

# Start working
git checkout -b feature/new-feature
# Make changes...
git add .
git commit -m "Add new feature"
git push origin feature/new-feature
# Create pull request on GitHub
```

---

### Option 2: Both Appear as Commit Authors

If code is already written and you want both names in commits:

#### Add Team Member as Co-Author:

```bash
git log --oneline

# For new commits, use co-author trailer:
git commit -m "Add feature

Co-authored-by: Team Member <team@example.com>"
```

#### Or Update Existing Commits:

```bash
# Interactive rebase
git rebase -i HEAD~5

# Edit commit message to add:
# Co-authored-by: Team Member <team@example.com>
```

---

### Option 3: Transfer Repository Ownership

If you want to make it a **joint repository**:

1. Go to Repository Settings
2. Scroll to "Danger Zone"
3. Click "Transfer" or "Make it a team repository"
4. Add team member to organization
5. Both appear as owners

---

## 📊 How Contributors Show Up

### On GitHub Profile:
- Commits appear on both profiles
- Contribution graph updates
- Shows in "Repositories" section
- Appears in contribution history

### Requirements:
- Commit uses correct GitHub email
- Account is public (or contributions are public)
- Commits are pushed to main branch

---

## ✅ Current Setup Instructions for Team Member

### 1. **Team Member's First Time Setup**

```bash
# Clone the repository
git clone https://github.com/Yashwantkashyap2005/Online-Exam-Management-System-.git
cd Online-Exam-Management-System

# Install backend dependencies
cd backend
npm install

# Install frontend dependencies (new terminal)
cd frontend
npm install

# Configure their git
git config user.name "Team Member Name"
git config user.email "team.member@github.com"

# Start backend
cd backend && npm start

# Start frontend (new terminal)
cd frontend && npm run dev
```

### 2. **Making Changes Together**

**Create Feature Branch:**
```bash
git checkout -b feature/feature-name
```

**Make Changes:**
```bash
# Edit files...
# Test locally...
```

**Commit Changes:**
```bash
git add .
git commit -m "Add feature description"
```

**Push to GitHub:**
```bash
git push origin feature/feature-name
```

**Create Pull Request:**
- Go to GitHub
- Click "Compare & Pull Request"
- Add description
- Click "Create Pull Request"
- Review and merge

### 3. **Both Appear as Contributors**

✅ **Automatically appears when:**
- Team member pushes commits using their GitHub account
- Commit email matches GitHub account email
- Pushed to the repository

✅ **Verify:**
- Go to GitHub repo → "Insights" → "Contributors"
- Both names should appear

---

## 🔧 Git Configuration for Team Members

### Set Up Global Config (One Time):
```bash
git config --global user.name "Team Member Name"
git config --global user.email "your.email@github.com"
```

### Set Up Local Config (Per Repository):
```bash
cd Online-Exam-Management-System
git config user.name "Team Member Name"
git config user.email "your.email@github.com"
```

### Verify Config:
```bash
git config --list
```

---

## 🚀 Collaboration Workflow

### 1. Main Branch (Production)
```
main ← Merged Pull Requests
```

### 2. Feature Branches
```
feature/auth
feature/exams
feature/grading
```

### 3. Workflow:
```
1. Create feature branch from main
2. Make changes and commit
3. Push to GitHub
4. Create Pull Request
5. Review code (optional)
6. Merge to main
7. Both appear as contributors
```

---

## 📝 Example: Adding Team Member's Contribution

### Scenario: Team member adds a new feature

**Step 1: Team Member Clones & Creates Branch**
```bash
git clone https://github.com/Yashwantkashyap2005/Online-Exam-Management-System-.git
cd Online-Exam-Management-System
git checkout -b feature/user-roles
```

**Step 2: Make Changes**
```bash
# Edit files in backend/models/User.js
# Edit files in frontend/src/components/
```

**Step 3: Commit & Push**
```bash
git add .
git commit -m "Add role management feature"
git push origin feature/user-roles
```

**Step 4: Create Pull Request on GitHub**
- Go to https://github.com/Yashwantkashyap2005/Online-Exam-Management-System-
- Click "Pull Requests" tab
- Click "New Pull Request"
- Select `feature/user-roles` → `main`
- Add description
- Click "Create Pull Request"

**Step 5: Merge (You approve)**
- Review changes
- Click "Merge Pull Request"
- Confirm merge

**Result:**
✅ Team member's commits appear on main  
✅ Team member appears in contributor list  
✅ Shows on both GitHub profiles

---

## 📊 Check Contributors

**View on GitHub:**
1. Go to repository
2. Click "Insights" (top menu)
3. Click "Contributors"
4. See all team members with commit counts

---

## 🎯 Best Practices

### ✅ Do:
- Use descriptive commit messages
- Create feature branches for each task
- Pull latest changes before starting
- Test locally before pushing
- Review each other's code

### ❌ Don't:
- Commit directly to main
- Force push to main
- Use unclear commit messages
- Ignore merge conflicts
- Skip testing

---

## 🔄 Resolving Merge Conflicts

If both team members edit same file:

```bash
# Update your branch
git pull origin main

# Fix conflicts in editor
# Files will have: <<<<<<<, =======, >>>>>>>

# After fixing:
git add .
git commit -m "Resolve merge conflict"
git push origin feature/branch-name
```

---

## 📱 Collaboration Tools

### GitHub
- Issues for bug tracking
- Pull requests for code review
- Discussions for ideas
- Projects for task management

### Examples:
```markdown
# Create issue
Title: Add email notifications
Labels: feature, enhancement

# Create discussion
Title: How should we handle user permissions?

# Use projects for workflow
Todo | In Progress | Done
```

---

## 🆘 Common Issues

### Issue: Team member's commits not showing

**Solution:**
```bash
# Verify git config
git config user.email

# Must match GitHub account email
# Update if needed:
git config user.email "correct@github.com"
```

### Issue: Can't push to repository

**Solution:**
```bash
# Check if you're a collaborator
# Ask owner to add you in Settings → Collaborators

# Verify credentials
git config --global credential.helper store
```

### Issue: Merge conflicts

**Solution:**
```bash
# Pull latest changes
git pull origin main

# Resolve conflicts in editor
# Commit resolved version
git add .
git commit -m "Resolve conflicts"
```

---

## 📋 Checklist for Team Collaboration

- [ ] Team member has GitHub account
- [ ] Added as collaborator (Settings → Collaborators)
- [ ] Team member accepted invitation
- [ ] Team member cloned repository
- [ ] Team member configured git (name, email)
- [ ] Team member can push changes
- [ ] Both appear in contributor list
- [ ] Pull request workflow established

---

## 🎉 Result

After following these steps:

✅ **Project shows on both GitHub profiles**  
✅ **Both appear as contributors**  
✅ **Both can see project in commit history**  
✅ **Collaboration is tracked**  
✅ **Contribution graph updates for both**  

---

## 📞 Support

If team member faces issues:
1. Check GitHub documentation
2. Review this guide
3. Create GitHub discussion
4. Contact support

---

**Happy collaborating! 🚀**
