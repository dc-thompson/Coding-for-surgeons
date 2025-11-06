# Quick Setup: Install 3 Things and Start Coding

> **Time:** 15-20 minutes  
> **Goal:** Get your computer ready for vibe coding

## What You're Installing

1. **Anaconda** - Python + data science packages (one-click install)
2. **VS Code** - Where you'll write/run code (think Microsoft Word for coding)
3. **Claude Code** - AI that writes code for you (your new best friend)

That's it. Three things. Then you're done.

---

## Step 1: Install Anaconda (5 minutes)

### What is Anaconda?

Anaconda is Python plus all the common data science tools pre-installed. Instead of installing 50 things separately, you install one thing.

**Surgical analogy:** It's like getting a pre-packed instrument tray instead of collecting individual instruments.

### Installation

**1. Download:**
- Go to: https://www.anaconda.com/download
- Click the big **Download** button
- It will auto-detect your operating system

**Important for Mac users:**
- If you have a newer Mac (2020+): Choose "Apple Silicon"
- If you have an older Mac: Choose "Intel"
- Not sure? Click Apple menu → About This Mac → look for "M1/M2/M3" or "Intel"

**2. Install:**
- **Windows:** Run the .exe file → Click "Next" repeatedly → Done
- **Mac:** Open the .pkg file → Click "Continue" repeatedly → Done

**3. Verify it worked:**

Open Terminal (Mac) or Command Prompt (Windows):

**Mac:** Press `Cmd + Space`, type "Terminal", press Enter  
**Windows:** Press `Windows key`, type "cmd", press Enter

Then type:
```bash
conda --version
```

You should see something like: `conda 23.7.4`

If you see that, **you're done with Step 1!** ✅

**If it doesn't work:**
- Close Terminal/Command Prompt
- **Restart your computer** (seriously, this fixes 90% of issues)
- Try again

---

## Step 2: Install VS Code (3 minutes)

### What is VS Code?

VS Code (Visual Studio Code) is where you'll write and run your code. It's like Microsoft Word, but for coding.

### Installation

**1. Download:**
- Go to: https://code.visualstudio.com/
- Click **Download** (it will auto-detect your OS)

**2. Install:**
- **Windows:** Run the .exe → Accept defaults → Install → Done
- **Mac:** Open the .dmg → Drag VS Code to Applications → Done

**3. Open it:**
- **Mac:** Applications → Visual Studio Code
- **Windows:** Start menu → Visual Studio Code

You should see a welcome screen. **You're done with Step 2!** ✅

---

## Step 3: Install Claude Code (7 minutes)

### What is Claude Code?

Claude Code is AI that writes code for you via the command line. You describe what you want, Claude writes it.

### Prerequisites

You need:
- **Claude Pro subscription** ($20/month)
- If you don't have it: Go to https://claude.ai/settings/billing

### Installation

**1. Install Node.js (if you don't have it):**

Check if you already have it:
```bash
node --version
```

**If you see a version number:** Skip to step 2!  
**If you see "command not found":** Install it:

- Go to: https://nodejs.org
- Download the **LTS version** (left button)
- Install (click through defaults)
- Restart Terminal/Command Prompt

**2. Install Claude Code:**

In Terminal (Mac) or Command Prompt (Windows), type:

```bash
npm install -g @anthropic-ai/claude-code
```

Wait 1-2 minutes while it installs.

**3. Get your API key:**

- Go to: https://claude.ai/settings/developer
- Click **"Create API Key"**
- Give it a name (like "My Laptop")
- Copy the key (starts with "sk-...")
- **SAVE THIS KEY SOMEWHERE SAFE** - you can't see it again!

**4. Connect Claude Code to your account:**

In Terminal/Command Prompt:

```bash
claude config
```

It will ask for your API key. Paste it and press Enter.

**5. Test it works:**

```bash
claude chat "Say hello"
```

Claude should respond with a greeting!

**You're done with Step 3!** ✅

---

## Step 4: Configure VS Code for Python (2 minutes)

**1. Open VS Code**

**2. Install Python extension:**
- Click the Extensions icon on the left sidebar (looks like 4 squares)
- Search for "Python"
- Find "Python" by Microsoft
- Click **Install**

**3. Set up Python interpreter:**
- Press `Ctrl/Cmd + Shift + P` (opens command palette)
- Type: "Python: Select Interpreter"
- Choose the one that says "anaconda3" or "conda"

**You're done!** ✅

---

## Verification Checklist

Before moving on, verify everything works:

**In Terminal/Command Prompt:**

```bash
# Check Anaconda
conda --version

# Check Python
python --version

# Check Claude Code
claude --version

# Test Claude
claude chat "What's 2+2?"
```

All four should work without errors.

**In VS Code:**
- ✅ Python extension installed
- ✅ Python interpreter selected (bottom left corner should show Python version)

---

## Troubleshooting

### "conda: command not found"

**Fix:** Restart your computer (seriously). The PATH doesn't update until restart.

If that doesn't work:

**Windows:**
- Search for "Anaconda Prompt"
- Use that instead of Command Prompt
- Everything should work there

**Mac:**
- Open Terminal
- Run: `source ~/anaconda3/bin/activate`
- Try `conda --version` again

### "npm: command not found"

You need to install Node.js:
- Go to: https://nodejs.org
- Download and install
- Restart Terminal/Command Prompt
- Try again

### "API key invalid"

Double-check:
- You have Claude Pro subscription (https://claude.ai/settings/billing)
- You copied the complete key (starts with "sk-ant-...")
- No extra spaces when pasting

Run `claude config` again to re-enter your key.

### VS Code can't find Python

1. Make sure Anaconda is installed
2. Restart VS Code
3. Press `Ctrl/Cmd + Shift + P`
4. Type: "Python: Select Interpreter"
5. Choose one with "anaconda3" in the path

---

## You're Ready!

**Congratulations!** You now have:
- ✅ Python and data science tools (Anaconda)
- ✅ A place to write code (VS Code)
- ✅ AI to help you code (Claude Code)

**Time to build your first project!**

→ **[Next: Your First Project](first-project.md)**

---

## Quick Reference

**To open Terminal/Command Prompt:**
- Mac: `Cmd + Space` → type "Terminal"
- Windows: `Windows key` → type "cmd"

**To start VS Code from a folder:**
```bash
cd /path/to/your/project
code .
```

**To ask Claude for help:**
```bash
claude chat "your question here"
```

**To have Claude edit a file:**
```bash
claude edit filename.py "what to change"
```

---

**Questions?** Claude can help! Just ask:

```bash
claude chat "How do I load a CSV file in Python?"
```

That's the beauty of vibe coding - when you forget, just ask Claude! 🎉
