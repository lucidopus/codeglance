# CodeGlance Quick Start Guide Prompt

You are a senior developer creating a "Get It Running in 5 Minutes" guide. Your goal is to get developers from zero to seeing the application work with minimal friction.

## Input Repository
Analyze the repository located at: [REPOSITORY_PATH]

## Your Mission
Create `guide/quick-start.md` - a step-by-step guide that gets the application running quickly with clear, copy-paste ready commands and proactive troubleshooting.

## Document Structure

### Header Section
```markdown
# 🚀 Quick Start Guide

> Get this running in 5 minutes or less! This guide provides the fastest path from clone to running application.

## ⏱️ Time Breakdown
- Prerequisites check: 30 seconds
- Clone and install: 1-2 minutes  
- Configuration: 1-2 minutes
- First run: 30 seconds
- Verify it works: 30 seconds

## 🎯 What You'll Have at the End
[Describe exactly what will be running and what they can do with it]
```

### Prerequisites Section
```markdown
## ✅ Prerequisites

Before you start, make sure you have:

### Required
- [ ] **[Tool]** (version X.X+) - Check with: `command --version`
- [ ] **[Tool]** (version X.X+) - Check with: `command --version`
- [ ] **[Resource]** - [How to get it if they don't have it]

### Optional (but recommended)
- [ ] **[Tool]** - [Why it helps]
- [ ] **[Tool]** - [Why it helps]

### Quick Install Commands
If you're missing requirements, here's how to get them:

**macOS:**
```bash
# Install [tool]
brew install [tool]
```

**Ubuntu/Debian:**
```bash
# Install [tool]
sudo apt-get install [tool]
```

**Windows:**
```bash
# Install [tool]
winget install [tool]
```
```

### Step-by-Step Instructions
```markdown
## 📝 Step-by-Step Instructions

### Step 1: Clone and Navigate (30 seconds)
```bash
# Clone the repository
git clone [repository-url]

# Navigate to the project
cd [project-name]

# Verify you're in the right place
ls  # You should see [key files/folders]
```

### Step 2: Install Dependencies (1-2 minutes)
```bash
# Install all dependencies
[install command]

# This installs:
# - [Major dependency 1] for [purpose]
# - [Major dependency 2] for [purpose]
# - [Number] other packages
```

💡 **Slow install?** Try `[alternative command]` for faster installation

### Step 3: Set Up Environment (1-2 minutes)

#### Option A: Quick Setup (Recommended)
```bash
# Copy the example environment file
cp .env.example .env

# The defaults will work for local development
```

#### Option B: Custom Setup
Create a `.env` file with your settings:
```bash
# Required variables
DATABASE_URL=postgresql://localhost/[dbname]  # Your database
API_KEY=your-api-key-here                     # Get from [where]
SECRET_KEY=any-random-string                  # Can be anything for dev

# Optional variables  
PORT=3000                                      # Change if 3000 is taken
DEBUG=true                                     # Enable debug logs
```

📝 **Need help with environment variables?** See [detailed explanation below]

### Step 4: Database Setup (if applicable)
```bash
# Create the database
[db create command]

# Run migrations
[migration command]

# (Optional) Seed with sample data
[seed command]
```

### Step 5: Run the Application! (30 seconds)
```bash
# Start the development server
[run command]

# You should see:
# [Expected output showing it's running]
# [URL where it's available]
```

🎉 **Success!** Open [http://localhost:3000](http://localhost:3000) in your browser

### Step 6: Verify Everything Works (30 seconds)

1. **Check the homepage**: You should see [description]
2. **Try feature X**: Click [button/link] and verify [result]
3. **Check the API**: Visit [http://localhost:3000/api/health](http://localhost:3000/api/health)
4. **Look at logs**: You should see [expected log entries]
```

### Common Issues & Solutions
```markdown
## 🔧 Troubleshooting

### Issue: Port already in use
```
Error: Port 3000 is already in use
```
**Solution:**
```bash
# Option 1: Use a different port
PORT=3001 [run command]

# Option 2: Find and kill the process using the port
lsof -i :3000  # Find the process
kill -9 [PID]  # Kill it
```

### Issue: Database connection failed
```
Error: Cannot connect to database
```
**Solution:**
```bash
# Make sure database is running
[command to check db status]

# If not running, start it
[command to start db]

# Verify connection string in .env
echo $DATABASE_URL
```

### Issue: Missing dependencies
```
Error: Cannot find module '[module]'
```
**Solution:**
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
[install command]
```

### Issue: Permission denied
```
Error: EACCES: permission denied
```
**Solution:**
```bash
# Fix permissions
chmod +x [file]
# Or run with proper permissions
sudo [command]
```

### Still stuck?
- Check the [FAQ](#-faq) below
- Look at [guide/troubleshooting.md](./troubleshooting.md)
- Search [existing issues](https://github.com/[repo]/issues)
- Ask in [Discord/Slack/Forum]
```

### Your First Changes
```markdown
## 🎨 Try Your First Change

Now that it's running, let's make a small change to see how development works:

### 1. Simple Visual Change
Edit `[file path]`:
```[language]
// Find this line (around line [X]):
[original code]

// Change it to:
[modified code]
```

Save the file and refresh your browser. You should see [expected change]!

### 2. Add a New Feature
Try adding a simple feature:
```[language]
// In [file path], add:
[code to add]
```

Now visit [URL] to see your new feature!

### 3. Run the Tests
Make sure everything still works:
```bash
[test command]
```

All tests should pass ✅
```

### Different Environments
```markdown
## 🌍 Other Environments

### Production Mode
```bash
# Build for production
[build command]

# Run production build
[production run command]
```

### Docker Setup
```bash
# Build and run with Docker
docker-compose up

# Access at http://localhost:3000
```

### Cloud Deployment
See [guide/deployment.md](./deployment.md) for:
- Deploying to [Platform 1]
- Deploying to [Platform 2]
- CI/CD setup
```

### Next Steps Section
```markdown
## 📚 Next Steps

Congratulations! You now have a working development environment. Here's what to explore next:

### Learn the Codebase
- 📖 **Understand the structure** → [guide/visual-tree.md](./visual-tree.md) (2 mins)
- 🏗️ **Learn the architecture** → [guide/architecture.md](./architecture.md) (10 mins)
- 📂 **Explore key files** → [guide/file-insights.md](./file-insights.md) (15 mins)

### Start Developing
- 💻 **Development workflow** → [guide/development.md](./development.md)
- 🧪 **Testing guide** → [guide/testing.md](./testing.md)
- 📝 **Contributing guidelines** → [CONTRIBUTING.md](../CONTRIBUTING.md)

### Get Help
- 💬 **Discord/Slack** → [invite link]
- 📚 **Documentation** → [docs link]
- ❓ **FAQ** → See below
```

### FAQ Section
```markdown
## ❓ FAQ

### Q: How do I reset everything and start fresh?
```bash
# Complete reset
rm -rf node_modules package-lock.json .env
[reinstall commands]
```

### Q: Can I use [alternative tool/version]?
A: Yes! [Explanation of compatibility]

### Q: How do I run this in [VS Code/other IDE]?
A: [IDE-specific instructions]

### Q: Where is the data stored?
A: [Explanation of data storage]

### Q: How do I add [common feature request]?
A: [Brief explanation or link to guide]
```

### Quick Reference Card
```markdown
## 📋 Quick Reference

### Essential Commands
```bash
# Install
[install command]

# Run development
[dev command]

# Run tests
[test command]

# Build
[build command]

# Clean
[clean command]
```

### Important Files
- `.env` - Environment configuration
- `[config file]` - Application settings
- `[main file]` - Entry point
- `[package file]` - Dependencies

### Default Ports & URLs
- Application: http://localhost:3000
- API: http://localhost:3000/api
- Database: localhost:5432
- [Other service]: [URL]
```

## Writing Guidelines

1. **Assume Nothing**: Don't assume any prior knowledge of the project
2. **Copy-Paste Ready**: Every command should work when copy-pasted
3. **Proactive Troubleshooting**: Address issues before they happen
4. **Time Estimates**: Let people know how long each step takes
5. **Success Indicators**: Show what success looks like at each step
6. **Multiple Options**: Provide alternatives when available
7. **Platform Awareness**: Include commands for different operating systems

## Success Metrics

After following this guide, a developer should:
- ✅ Have the application running locally
- ✅ Have made and seen a small change
- ✅ Understand basic commands
- ✅ Know where to get help
- ✅ Feel confident to explore further

Generate the quick-start.md for [REPOSITORY_PATH] now.