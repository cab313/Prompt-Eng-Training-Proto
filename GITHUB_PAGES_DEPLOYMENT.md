# 🚀 GitHub Pages Deployment - Step-by-Step Guide

This guide will walk you through deploying the Prompt Engineering Battle Royale to GitHub Pages so your team can access it via a URL.

## 📋 Prerequisites

Before starting, ensure you have:
- ✅ Git installed on your Mac (check by running `git --version` in Terminal)
- ✅ A GitHub account
- ✅ All project files in the `Prompt Eng Training Proto` folder

---

## 🎯 Step-by-Step Deployment

### Step 1: Install Git (if not already installed)

Open Terminal and check if Git is installed:

```bash
git --version
```

If you see a version number (e.g., `git version 2.39.0`), Git is installed. ✅

If not installed, run:
```bash
xcode-select --install
```

---

### Step 2: Navigate to Your Project Folder

In Terminal, navigate to your project:

```bash
cd "/Users/cbrondon/Downloads/Prompt Eng Training Proto"
```

Verify you're in the right folder:
```bash
ls
```

You should see: `index.html`, `css/`, `js/`, `data/`, etc.

---

### Step 3: Initialize Git Repository

Initialize a new Git repository:

```bash
git init
```

You should see: `Initialized empty Git repository`

---

### Step 4: Add All Files to Git

Add all project files:

```bash
git add .
```

Check what will be committed:

```bash
git status
```

You should see all your files listed in green.

---

### Step 5: Create Initial Commit

Commit your files:

```bash
git commit -m "Initial commit: Prompt Engineering Battle Royale"
```

You should see a summary of files added.

---

### Step 6: Create GitHub Repository

Now go to GitHub in your web browser:

1. **Go to GitHub**: https://github.com
2. **Sign in** to your account
3. **Click the "+" icon** in the top-right corner
4. **Select "New repository"**

Fill in the details:
- **Repository name**: `prompt-battle-royale` (or any name you prefer)
- **Description**: "Interactive Prompt Engineering Training Game"
- **Visibility**:
  - Choose **Public** for regular GitHub
  - Or **Private** if using GitHub Enterprise (teammates will need access)
- **DO NOT** check "Initialize this repository with a README"
- **Click "Create repository"**

---

### Step 7: Connect Local Repository to GitHub

GitHub will show you commands. Use the "push an existing repository" section.

Copy the repository URL (it looks like):
- `https://github.com/yourusername/prompt-battle-royale.git`

Back in Terminal, run:

```bash
git remote add origin https://github.com/yourusername/prompt-battle-royale.git
```

Replace `yourusername` and `prompt-battle-royale` with your actual GitHub username and repository name.

---

### Step 8: Rename Branch to Main (if needed)

GitHub Pages works best with the `main` branch:

```bash
git branch -M main
```

---

### Step 9: Push to GitHub

Push your code to GitHub:

```bash
git push -u origin main
```

You may be asked to authenticate:
- Enter your GitHub username
- Enter your personal access token (not password - see below if needed)

**If you need a personal access token:**
1. Go to GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Click "Generate new token (classic)"
3. Give it a name: "Prompt Battle Deployment"
4. Check the "repo" scope
5. Click "Generate token"
6. Copy the token and use it as your password

---

### Step 10: Enable GitHub Pages

1. **Go to your repository** on GitHub
2. **Click "Settings"** tab (near the top)
3. **Scroll down** and click **"Pages"** in the left sidebar
4. Under **"Source"**:
   - Select branch: **`main`**
   - Select folder: **`/ (root)`**
5. **Click "Save"**

You'll see a message: "Your site is ready to be published at..."

---

### Step 11: Wait for Deployment

GitHub Pages takes 2-5 minutes to build and deploy.

After waiting, refresh the Settings → Pages page.

You should see:
```
✅ Your site is live at https://yourusername.github.io/prompt-battle-royale/
```

---

### Step 12: Test Your Deployment

1. **Click the URL** or copy/paste it into your browser
2. **Test the application**:
   - Create a profile
   - Complete a battle
   - Check all features work
3. **Test on mobile** (if applicable)

---

### Step 13: Share with Your Team

Once everything works, share the URL with your team:

```
🎮 Prompt Engineering Battle Royale is now live!

Access the training game at:
https://yourusername.github.io/prompt-battle-royale/

Get started:
1. Click the link
2. Create your profile
3. Start battling!

May the best prompt win! 🏆
```

---

## 🔄 Making Updates

When you make changes to the application:

### Update Process:

```bash
# 1. Navigate to project folder
cd "/Users/cbrondon/Downloads/Prompt Eng Training Proto"

# 2. Check what changed
git status

# 3. Add changes
git add .

# 4. Commit with a descriptive message
git commit -m "Update: Added new scenarios and fixed timer bug"

# 5. Push to GitHub
git push origin main

# 6. Wait 2-3 minutes for GitHub Pages to update
```

Your site will automatically update! ✨

---

## 🛠️ Troubleshooting

### Issue: "Permission denied (publickey)"

**Solution**: Use HTTPS instead of SSH for the remote URL:

```bash
git remote set-url origin https://github.com/yourusername/prompt-battle-royale.git
```

### Issue: "Repository not found"

**Solution**: Check your repository name and username:

```bash
# Check current remote
git remote -v

# Update if needed
git remote set-url origin https://github.com/CORRECT-username/CORRECT-repo.git
```

### Issue: Pages shows 404 error

**Solutions**:
1. Wait 5 more minutes (deployment can be slow)
2. Check Settings → Pages shows the site is live
3. Clear browser cache (Cmd+Shift+R)
4. Make sure `index.html` is in the root folder
5. Check repository visibility (must be Public or teammates must have access)

### Issue: Images/CSS not loading

**Solution**: This usually happens with incorrect file paths. The app uses relative paths (`./css/`, `./js/`) which should work. If issues persist:

1. Check browser console (F12) for errors
2. Verify all files were pushed to GitHub
3. Check file paths are relative, not absolute

### Issue: API calls failing

**Solution**:
1. Check browser console for CORS errors
2. Ensure the API endpoint (`https://api.wearables-ape.io`) is accessible
3. Verify API key is in the code (it should be)

---

## 🔒 For GitHub Enterprise (Internal Deployment)

If using GitHub Enterprise for internal company use:

### Step 1: Use Company GitHub

Instead of github.com, use your company's GitHub:
```
https://github.yourcompany.com
```

### Step 2: Create Repository in Enterprise

1. Go to your company's GitHub Enterprise instance
2. Create repository as normal
3. Set appropriate visibility (Internal/Private)

### Step 3: Use Enterprise URL

```bash
git remote add origin https://github.yourcompany.com/yourusername/prompt-battle-royale.git
```

### Step 4: Enable Pages

GitHub Enterprise Pages may be at:
```
https://pages.github.yourcompany.com/yourusername/prompt-battle-royale/
```

Or:
```
https://yourusername.github.yourcompany.com/prompt-battle-royale/
```

Check with your IT department for the exact URL format.

---

## 📱 Custom Domain (Optional)

If you want a custom domain like `prompt-battle.yourcompany.com`:

1. **Settings → Pages → Custom domain**
2. Enter your domain name
3. Click "Save"
4. Configure DNS (ask IT department):
   - Add CNAME record pointing to `yourusername.github.io`
   - Wait for DNS propagation (up to 24 hours)

---

## 🎉 Success Checklist

- [x] Git repository initialized
- [x] Files committed to Git
- [x] GitHub repository created
- [x] Code pushed to GitHub
- [x] GitHub Pages enabled
- [x] Site is live and accessible
- [x] All features tested and working
- [x] Team has been notified with URL
- [x] Leaderboard sync process documented

---

## 📊 Monitoring Your Deployment

### Check Deployment Status

Visit your repository → **Actions** tab (if available) to see deployment status.

### View Analytics

Your Google Analytics (G-Q98010P7LZ) will track:
- Page views
- User sessions
- Battle completions
- Feature usage

Access at: https://analytics.google.com

---

## 🆘 Getting Help

### GitHub Documentation
- [GitHub Pages Guide](https://docs.github.com/pages)
- [Git Basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)

### Common Git Commands

```bash
# Check status
git status

# View remote URL
git remote -v

# View commit history
git log --oneline

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Pull latest changes (if collaborating)
git pull origin main

# Create a new branch
git checkout -b feature-name

# Switch branches
git checkout main
```

---

## 🎊 You're Done!

Your Prompt Engineering Battle Royale is now live on GitHub Pages! 🎉

**Your URL**: `https://yourusername.github.io/prompt-battle-royale/`

Share it with your team and start training! 🚀

---

## 📝 Quick Reference Card

```bash
# Initial Setup (do once)
cd "/Users/cbrondon/Downloads/Prompt Eng Training Proto"
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/username/repo.git
git branch -M main
git push -u origin main

# Future Updates (repeat as needed)
git add .
git commit -m "Your update message"
git push origin main
```

**Enable Pages**: Settings → Pages → Source: main / (root) → Save

**Wait**: 2-5 minutes for deployment

**Access**: https://username.github.io/repo-name/

---

*Happy deploying! Your team will love this! 🎮*
