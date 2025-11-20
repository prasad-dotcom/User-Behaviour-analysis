# Git Workflow Guide for User Behavior Tracker Project

## 🚀 Quick Commands Reference

### Initial Setup (One-time)
```bash
# Navigate to your project
cd "C:\Users\Prasad reddy\OneDrive\Desktop\User Behaviour tracker"

# Initialize git repository (if not already done)
git init

# Add remote repository
git remote add origin https://github.com/dev-rathankumar/greatkart-pre-deploy.git

# Set your git credentials
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

### Daily Workflow

#### 1. Check Status
```bash
# See what files have changed
git status

# See what specific changes were made
git diff
```

#### 2. Stage Files
```bash
# Add specific files
git add filename.py
git add folder/

# Add all files (be careful!)
git add .

# Add all modified files (not new files)
git add -u
```

#### 3. Commit Changes
```bash
# Commit with a message
git commit -m "Your descriptive commit message"

# Commit all modified files with message
git commit -am "Your commit message"
```

#### 4. Push to Remote
```bash
# Push to main branch
git push origin main

# Push and set upstream (first time)
git push -u origin main
```

## 📋 Complete Workflow for Your Project

### Step 1: Check Current Status
```powershell
cd "C:\Users\Prasad reddy\OneDrive\Desktop\User Behaviour tracker"
git status
```

### Step 2: Stage Important Files
```powershell
# Main project documentation
git add README.md
git add TRACKING_VERIFICATION_REPORT.md
git add .gitignore

# Navigate to Django project
cd greatkart

# Add tracking system files
git add tracking/
git add templates/tracking/
git add static/js/userBehaviour.js
git add static/js/userBehaviour.min.js
git add greatkart/tracking_views.py
git add greatkart/settings.py
git add greatkart/urls.py
git add templates/base.html
git add test_tracking.py
```

### Step 3: Commit Changes
```powershell
# In greatkart directory
git commit -m "Add comprehensive user behavior tracking system

Features added:
- Complete tracking system with JavaScript frontend and Django backend
- Real-time data collection for user interactions
- Analytics dashboard with visualizations
- Database models for sessions, logs, and e-commerce events
- API endpoints for data collection
- Debug and test pages
- Error handling and console logging"

# Go back to main directory
cd ..
git commit -m "Add project documentation and configuration files"
```

### Step 4: Push to GitHub
```powershell
# From greatkart directory
cd greatkart
git push origin main

# From main directory
cd ..
git push origin main
```

## 🔧 Troubleshooting Common Issues

### Permission Denied (403 Error)
If you get a 403 permission error:

1. **Check Repository Access:**
   - Make sure you have write access to the repository
   - Verify you're pushing to the correct repository URL

2. **Update Remote URL (if needed):**
   ```bash
   # Check current remote
   git remote -v
   
   # Update to use SSH (if you have SSH keys set up)
   git remote set-url origin git@github.com:dev-rathankumar/greatkart-pre-deploy.git
   
   # Or update to use your username in HTTPS URL
   git remote set-url origin https://prasad-dotcom@github.com/dev-rathankumar/greatkart-pre-deploy.git
   ```

3. **Use Personal Access Token:**
   ```bash
   # When prompted for password, use your GitHub Personal Access Token
   # instead of your GitHub password
   ```

### Large Files or Media Files
```bash
# Remove large files from staging
git reset HEAD media/photos/

# Add media files to .gitignore to prevent future commits
echo "media/photos/*.jpg" >> .gitignore
echo "media/photos/*.png" >> .gitignore
```

### Undo Last Commit (if needed)
```bash
# Undo last commit but keep changes
git reset --soft HEAD~1

# Undo last commit and discard changes (DANGEROUS!)
git reset --hard HEAD~1
```

## 📊 Your Current Repository Status

### ✅ Successfully Committed:
- User behavior tracking system (33 files, 4086 insertions)
- Project documentation (README.md, verification report)
- Configuration files (.gitignore)

### 🔄 What's Been Done:
1. ✅ All tracking system files committed in `greatkart/` subdirectory
2. ✅ Documentation files committed in main directory
3. ✅ Proper .gitignore file created
4. ⚠️ Push to remote may need authentication resolution

### 🎯 Next Steps:
1. **Resolve GitHub Authentication** (see troubleshooting section above)
2. **Push Remaining Changes:**
   ```bash
   git push origin main
   ```
3. **Verify on GitHub:** Check that all files appear in your GitHub repository

## 📝 Best Practices Going Forward

### Commit Message Format:
```
Type: Brief description

- Detailed change 1
- Detailed change 2
- Detailed change 3
```

### Commit Frequently:
- Make small, focused commits
- Commit working features/fixes immediately
- Don't wait until end of day to commit everything

### Before Major Changes:
```bash
# Create a backup branch
git checkout -b backup-branch-name

# Make your changes, then merge back
git checkout main
git merge backup-branch-name
```

### Keep Repository Clean:
- Use .gitignore for sensitive files, logs, cache files
- Don't commit virtual environments (cenv/, venv/)
- Don't commit database files (*.sqlite3)
- Don't commit large media files unless necessary

## 🎉 Congratulations!
Your user behavior tracking system is now version-controlled and (mostly) pushed to GitHub! 
The system includes comprehensive tracking, analytics, and documentation.