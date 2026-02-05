# Step-by-Step Guide - After Accepting Collaborator Invitation

## 🎉 आपके दोस्त ने Invitation Accept कर दी है!

अब दोनों को यह करना है:

---

## 📋 Complete Workflow

### **Phase 1: Initial Setup (एक बार, दोनों को)**

#### Step 1: Repository Clone करना (दोस्त के लिए)

```bash
# अपने computer पर जाओ
cd Desktop

# Repository clone करो
git clone https://github.com/Yashwantkashyap2005/Online-Exam-Management-System-.git
cd Online-Exam-Management-System
```

**Output होना चाहिए:**
```
Cloning into 'Online-Exam-Management-System'...
remote: Enumerating objects: 100%
...
done.
```

#### Step 2: Dependencies Install करना (दोस्त के लिए)

**Terminal 1 - Backend:**
```bash
cd backend
npm install
```

**Output:**
```
added 101 packages in 5s
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm install
```

**Output:**
```
added 226 packages in 8s
```

#### Step 3: Git Configuration (दोस्त के लिए - बहुत important!)

```bash
# अपना नाम set करो
git config user.name "दोस्त का नाम"

# अपना GitHub email set करो (जो GitHub account में registered है)
git config user.email "dost@github.com"

# Verify करो कि सब सही है
git config --list
```

**Output verify करना:**
```
user.name=दोस्त का नाम
user.email=dost@github.com
```

---

## 🚀 Phase 2: काम करना शुरू करो (दोनों को)

### **Step 1: Latest Code Update करना**

दोनों को सुबह सबसे पहले यह करना है:

```bash
# Main branch पर आओ
git checkout main

# Latest changes pull करो
git pull origin main
```

### **Step 2: नई Feature के लिए Branch बनाओ**

```bash
# नई branch बनाओ (descriptive नाम दो)
git checkout -b feature/your-feature-name

# Examples:
# git checkout -b feature/add-proctoring
# git checkout -b feature/fix-login-bug
# git checkout -b feature/exam-timer
```

### **Step 3: Code Edit करो**

```bash
# अपना feature develop करो
# Files edit करो
# Test करो locally

# Backend start करो (नया Terminal):
cd backend
npm start

# Frontend start करो (अलग Terminal):
cd frontend
npm run dev
```

### **Step 4: Changes को Commit करो**

```bash
# सब files को stage करो
git add .

# Commit करो (descriptive message दो)
git commit -m "Add feature: description of what you did"

# Examples:
# git commit -m "Add webcam proctoring check"
# git commit -m "Fix login validation bug"
# git commit -m "Implement exam timer feature"
```

**Output:**
```
[feature/your-feature b1c2d3e] Add feature: description
 5 files changed, 150 insertions(+)
```

### **Step 5: GitHub पर Push करो**

```bash
# अपनी branch को GitHub पर push करो
git push origin feature/your-feature-name
```

**Output:**
```
Counting objects: 7, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 456 bytes, done.
Total 4 (delta 2), reused 0 (delta 0)
To https://github.com/Yashwantkashyap2005/Online-Exam-Management-System-.git
 * [new branch]      feature/your-feature-name -> feature/your-feature-name
```

---

## 🔄 Phase 3: Pull Request बनाना

### **Step 1: GitHub पर जाओ**

Link खोलो:
```
https://github.com/Yashwantkashyap2005/Online-Exam-Management-System-
```

### **Step 2: Pull Request बनाओ**

1. GitHub खोलो
2. "Pull Requests" tab click करो
3. "New Pull Request" button दबाओ
4. Base: `main` select करो
5. Compare: `feature/your-feature-name` select करो
6. "Create Pull Request" button दबाओ

### **Step 3: PR Description Fill करो**

```markdown
## Description
क्या किया है का description लिखो

## Changes Made
- Change 1
- Change 2
- Change 3

## Testing Done
Locally test किया है या नहीं बताओ

## Type of Change
- [ ] Bug fix
- [x] New feature
- [ ] Breaking change
```

---

## ✅ Phase 4: Merge करना (आप करोगे)

### **Step 1: Code Review करो**

1. PR को देखो
2. Changes को review करो
3. Comment दो अगर कुछ change करना हो

### **Step 2: Merge करो**

1. "Merge pull request" button दबाओ
2. "Confirm merge" दबाओ
3. "Delete branch" दबाओ (optional)

**Result:**
```
Pull request successfully merged and closed
✓ You can safely delete this branch
```

---

## 🔄 Phase 5: Main को Update करना (दोनों को)

Merge होने के बाद, दोनों को अपने local main को update करना है:

```bash
# Main branch पर आओ
git checkout main

# Latest changes pull करो
git pull origin main

# Old branch delete करो (optional)
git branch -d feature/your-feature-name
```

---

## 📊 Check करो - दोनों Contributor दिखें या नहीं

### **GitHub पर Check करो:**

1. Repository खोलो
2. "Insights" tab click करो
3. "Contributors" click करो
4. दोनों के नाम दिखने चाहिए

### **Command से Check करो:**

```bash
git log --oneline --all
```

Output:
```
b1c2d3e (HEAD -> main) Add feature: description (दोस्त का नाम)
a1b2c3d (origin/main) Add feature: description (आपका नाम)
...
```

---

## 🔁 Day-to-Day Workflow

### **हर दिन शुरुआत में:**

```bash
# Latest update करो
git pull origin main

# अपनी branch बनाओ
git checkout -b feature/new-thing
```

### **दिन भर में:**

```bash
# Changes commit करो (बार बार)
git add .
git commit -m "Working on feature"
git push origin feature/new-thing
```

### **Feature complete होने पर:**

```bash
# Final commit करो
git add .
git commit -m "Complete feature: description"
git push origin feature/new-thing

# GitHub पर PR create करो
# दोस्त से review करवाओ (optional)
# Merge करो
```

---

## ⚠️ Conflicts होने पर क्या करें?

अगर दोनों एक ही file edit करो तो:

### **Step 1: Latest Update करो**

```bash
git pull origin main
```

**Error आएगी:**
```
CONFLICT (content): Merge conflict in filename
Automatic merge failed; fix conflicts and then commit.
```

### **Step 2: File को Fix करो**

File open करो, तुम्हें दिखेगा:

```
<<<<<<< HEAD
आपका code
=======
दोस्त का code
>>>>>>> main
```

अपनी पसंद का रखो, दोनों को combine करो, या एक को delete करो।

### **Step 3: Resolve करो**

```bash
# File को fix करो
# फिर:
git add filename
git commit -m "Resolve merge conflict"
git push origin feature/branch-name
```

---

## ✨ Best Practices

### ✅ करो:

```bash
# Commits छोटी-छोटी रखो
git commit -m "Add login validation"

# Regular push करो
git push origin feature/branch

# Pull करते रहो
git pull origin main

# Descriptive branch names रखो
git checkout -b feature/user-authentication
```

### ❌ न करो:

```bash
# Main को directly edit न करो
git checkout main
git add .
git commit -m "Some random changes"

# Force push न करो
git push -f origin main

# Big commits न करो
git commit -m "Fixed everything"

# Unclear messages न दो
git commit -m "xyz"
```

---

## 🎯 Example: Complete Workflow

### **आज का काम:**

```bash
# 1. सुबह latest update करो
git pull origin main

# 2. नई branch बनाओ - proctoring feature के लिए
git checkout -b feature/add-proctoring

# 3. Code edit करो
# - backend/models/Exam.js edit करो
# - frontend/components/ProctorChecks.jsx edit करो

# 4. Local test करो
npm start (backend terminal)
npm run dev (frontend terminal)

# 5. Changes commit करो
git add .
git commit -m "Add webcam proctoring feature"

# 6. GitHub पर push करो
git push origin feature/add-proctoring

# 7. GitHub पर PR बनाओ
# - Browser खोलो
# - "Pull Requests" → "New PR"
# - Description fill करो
# - "Create Pull Request" दबाओ

# 8. दोस्त से review करवाओ (optional comment में)

# 9. Merge करो
# - "Merge pull request" दबाओ

# 10. Local main update करो
git checkout main
git pull origin main
git branch -d feature/add-proctoring
```

---

## 📊 GitHub Profile पर दिखना

**दोनों को दिखेगा:**

✅ Repository अपने profile पर  
✅ Commits अपने profile पर  
✅ Contribution graph update होगा  
✅ "Repositories" section में project  
✅ Contribution count बढ़ेगी  

---

## 🆘 Common Issues

### Issue: "Permission denied"

```
ERROR: Permission denied (publickey)
```

**Fix:**
```bash
# SSH key setup करना है
# या HTTPS use करना है
git clone https://github.com/... (HTTPS से)
```

### Issue: "Branch diverged"

```
error: failed to push some refs
```

**Fix:**
```bash
git pull origin main
# Conflicts resolve करो
git push origin feature/branch
```

### Issue: "File not staged for commit"

```
Changes not staged for commit:
```

**Fix:**
```bash
git add .  # सब files add करो
git commit -m "message"
git push origin branch
```

---

## 📝 Checklist - हर Feature के लिए

- [ ] Latest code pull किया
- [ ] नई branch बनाई
- [ ] Code edit और test किया
- [ ] Commit descriptive message के साथ
- [ ] GitHub पर push किया
- [ ] PR बनाया और description दिया
- [ ] दोस्त से review करवाया (optional)
- [ ] Merge किया
- [ ] Local main update किया
- [ ] Old branch delete की

---

## 🎉 Final Result

After following this:

✅ दोनों names GitHub पर contributor के रूप में दिखेंगे  
✅ दोनों के GitHub profile पर project होगा  
✅ दोनों का contribution count बढ़ेगा  
✅ Proper collaboration workflow होगी  
✅ Code changes properly tracked होंगी  

---

## 📞 Reference Commands

```bash
# Basic commands
git status                    # Status check करो
git log                       # Commit history देखो
git branch                    # सब branches देखो
git pull origin main          # Main update करो
git push origin branch-name   # अपनी branch push करो

# Advanced
git diff                      # Changes देखो
git reset HEAD filename       # File unstage करो
git stash                     # Changes temporarily save करो
git rebase main              # Branch को main के साथ update करो
```

---

**Happy Coding Together! 🚀**

अगर कोई issue आए तो यह file में देखो या GitHub Discussions में पूछो!
