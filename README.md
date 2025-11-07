# Vibe Coding for Surgeons

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)

---

**This Repository:** A quick guide + working example for data analysis using a vibe-coding strategy

---

## Quick Start (5 Minutes)

Start here:

1. **Clone or download** this repository
2. **Navigate to** `example-project/`
3. **Open** `analysis.ipynb` in VS Code or Jupyter
4. **Click** "Run All"
5. **Check** the `results/` folder for publication-ready outputs

**You should have just completed a surgical complication analysis**

Use this as a guiderail and start playing with your own data.

---

## What's Included

This repository contains **two learning resources:**

### 1. Simplified Guide (`vibe-coding-simplified/`)

A 6-file guide that teaches you:
- ✅ The vibe coding philosophy ("AI codes, you think")
- ✅ How to install tools (Anaconda, VS Code, Claude Code)
- ✅ How to structure analysis projects
- ✅ How to communicate effectively with AI
- ✅ Complete walkthrough of a real analysis

**Time investment:** 1-2 hours to read

### 2. 💻 Working Example (`example-project/`)

A complete, ready-to-run Jupyter notebook with:
- ✅ Pre-filled analysis code (just click "Run All")
- ✅ Sample surgical data (120 cases, 4 procedures)
- ✅ Statistical tests (Chi-square, logistic regression)
- ✅ Publication-quality visualizations
- ✅ Automated export of results

**Time investment:** 5 minutes to see it work

---

## 🚀 Two Learning Paths

Choose based on your style:

### Path A: Do First, Learn Later

**Best for:** People who learn by doing

1. **Run the example** (`example-project/analysis.ipynb`) → 5 min
2. **See complete results** → Instant confidence! 🎉
3. **Read the guide** to understand what happened → 1 hour
4. **Modify the example** gradually → 30 min
5. **Apply to your data** → 30 min

**Total time:** 2 hours | **Result:** Analyzing your own data

### Path B: Learn First, Then Do (Traditional 📚)

**Best for:** People who prefer to understand before acting

1. **Read the guide** (`vibe-coding-simplified/`) → 1 hour
2. **Install the tools** (Anaconda, VS Code, Claude Code) → 15 min
3. **Run the example** to see it in action → 5 min
4. **Modify and experiment** → 30 min
5. **Apply to your data** → 30 min

**Total time:** 2 hours | **Result:** Analyzing your own data

---

## 📖 Repository Structure

```
vibe-coding-for-surgeons/
│
├── README.md                          # 👈 You are here
│
├── vibe-coding-simplified/            # 📚 The Guide
│   ├── README.md                      # Start here for philosophy
│   ├── GUIDE_NAVIGATION.md            # How to navigate the guide
│   └── docs/
│       ├── quick-setup.md            # Install Anaconda, VS Code, Claude Code
│       ├── first-project.md          # Project structure & organization
│       ├── talking-to-claude.md      # CRISP framework for AI prompts
│       └── example-analysis.md       # Written walkthrough
│
└── example-project/                   # 💻 Working Example
    ├── README.md                      # How to use this example
    ├── analysis.ipynb                # 📓 Complete notebook - run this!
    ├── data/
    │   └── surgical_data.csv         # Sample data (120 cases)
    └── results/                      # Generated automatically
        ├── figures/                  # PNG charts (300 DPI)
        └── tables/                   # CSV tables
```

---

## Learning objectives

After completing this guide, you'll be able to:

✅ Load surgical data (CSV, Excel, etc.)  
✅ Calculate complication rates with confidence intervals  
✅ Perform statistical tests (Chi-square, t-tests, etc.)  
✅ Build logistic regression models  
✅ Create publication-quality figures  
✅ Export results for papers and presentations  
✅ Use AI to write code effectively

**And most importantly:** Continue learning by asking Claude when you need something new!

---

## 🎓 Prerequisites

### What You Need:

**Required:**
- 💻 Computer (Mac or Windows)
- 💳 [Claude Pro subscription](https://claude.ai/settings/billing) ($20/month)
- 📊 Your de-identified surgical data
- ⏰ 2 hours of time

**Free:**
- [Anaconda](https://www.anaconda.com/download) (Python + data science packages)
- [VS Code](https://code.visualstudio.com/) (coding environment)
- This repository!

### What You DON'T Need:

❌ Prior programming experience  
❌ Computer science degree  
❌ Months of Python courses  
❌ Perfect memory of syntax  

**Claude handles the coding. You handle the thinking.**

---

## 🏃 Getting Started

### Step 1: Install Prerequisites

Follow the detailed instructions in [`vibe-coding-simplified/docs/quick-setup.md`](vibe-coding-simplified/docs/quick-setup.md)

**Summary:**
1. Install [Anaconda](https://www.anaconda.com/download)
2. Install [VS Code](https://code.visualstudio.com/)
3. Install Claude Code: `npm install -g @anthropic-ai/claude-code`
4. Configure: `claude config` (enter your API key)

**Time:** 15-20 minutes

### Step 2: Run the Example

```bash
# Clone this repository
git clone https://github.com/yourusername/vibe-coding-for-surgeons.git
cd vibe-coding-for-surgeons

# Open the example project
cd example-project
code .  # Opens VS Code

# Open analysis.ipynb and click "Run All"
```

**Time:** 5 minutes

### Step 3: Read the Guide

Start with [`vibe-coding-simplified/README.md`](vibe-coding-simplified/README.md)

**Time:** 1 hour

### Step 4: Adapt to Your Data

Replace `example-project/data/surgical_data.csv` with your own data and modify the notebook.

**Time:** 30 minutes

---

## 🔬 Example Output

**What the example notebook generates:**

### Tables (CSV format)
- `complication_rates.csv` - Rates by procedure with 95% CI
- `risk_factors.csv` - Logistic regression odds ratios

### Figures (300 DPI PNG)
- `complication_rates.png` - Bar chart with error bars
- `forest_plot.png` - Odds ratios visualization

**All ready for your paper or presentation!**

---

## 📚 Detailed Guide Contents

### [`vibe-coding-simplified/`](vibe-coding-simplified/)

1. **[README.md](vibe-coding-simplified/README.md)** (5 min read)
   - Philosophy: "AI codes, you think"
   - What you'll learn
   - Safety warnings (Patient data, verification)

2. **[docs/quick-setup.md](vibe-coding-simplified/docs/quick-setup.md)** (15 min to do)
   - Install Anaconda, VS Code, Claude Code
   - Verification checklist
   - Troubleshooting

3. **[docs/first-project.md](vibe-coding-simplified/docs/first-project.md)** (10 min to do)
   - Project structure template
   - Jupyter notebook basics
   - Organizing your work

4. **[docs/talking-to-claude.md](vibe-coding-simplified/docs/talking-to-claude.md)** (10 min read)
   - CRISP framework for prompts
   - Good vs bad prompts
   - Common scenarios
   - Tips and tricks

5. **[docs/example-analysis.md](vibe-coding-simplified/docs/example-analysis.md)** (30 min read)
   - Complete written walkthrough
   - Step-by-step instructions
   - Expected outputs
   - How to adapt

---

## 💻 Working Example Details

### [`example-project/`](example-project/)

**What's included:**
- Complete Jupyter notebook with pre-written code
- Sample surgical data (120 cases, 4 procedures)
- Markdown explanations in each cell
- Comments showing where to adapt for your data
- Professional styling throughout

**What it analyzes:**
- Descriptive statistics
- Complication rates by procedure
- Statistical significance testing
- Risk factor analysis (logistic regression)
- Publication-quality visualizations

**How to use it:**
1. Open `analysis.ipynb`
2. Run all cells (click "Run All")
3. Examine outputs in `results/`
4. Modify incrementally to learn
5. Replace data with your own
6. Customize analyses as needed

**Full instructions:** [`example-project/README.md`](example-project/README.md)

---

## 🎓 The Vibe Coding Philosophy

### You Are the Attending

Think of AI (Claude) as your surgical resident:
- ✅ Fast and knowledgeable
- ✅ Handles tedious work
- ✅ Suggests approaches
- ❌ But needs supervision
- ❌ And requires verification

**YOU make the clinical/scientific decisions.**  
**CLAUDE writes the code.**  
**TOGETHER you get results fast.**

### The CRISP Framework

When asking Claude for code, use this template:

**C**ontext - What are you working with?  
**R**equirements - What must it do?  
**I**nputs - What data format?  
**S**pecifics - Edge cases, preferences  
**P**urpose - Why are you doing this?

**Example:**
```bash
claude edit analysis.py "
Context: Analyzing post-operative complications from surgical database
Requirements: Load CSV, calculate rates, create bar chart
Inputs: CSV file with columns: patient_id, procedure, complication
Specifics: Use Wilson score for 95% CI, handle missing data
Purpose: Quality improvement presentation next week
"
```

This gives Claude everything needed for excellent code!

---

## ⚠️ Safety & Best Practices

### Information Governance Compliance

**⚠️ CRITICAL:** Never upload identifiable patient data to Claude!

**Before using your data:**
- ✅ De-identify all patient information
- ✅ Remove names, MRNs, dates of birth
- ✅ Use patient IDs instead of identifiers
- ✅ Use relative dates, not absolute dates
- ✅ Check your institution's data policies

### Code Review

**Always review AI-generated code:**
- ✅ Does the logic make sense?
- ✅ Are statistical methods appropriate?
- ✅ Do results align with clinical expectations?
- ✅ Test on small subsets first

**Remember:** You're the attending, Claude is the resident!

### Version Control

**Use Git to save your work:**
```bash
git init
git add .
git commit -m "Initial analysis"
```

Create checkpoints as you make progress.

---

## 🆘 Troubleshooting

### Installation Issues

**"conda: command not found"**
- Restart your computer (PATH needs to update)
- Or use Anaconda Prompt (Windows) instead of Command Prompt

**"npm: command not found"**
- Install [Node.js](https://nodejs.org) first
- Then install Claude Code

**Full troubleshooting:** See [`vibe-coding-simplified/docs/quick-setup.md#troubleshooting`](vibe-coding-simplified/docs/quick-setup.md)

### Example Won't Run

**Check:**
1. Are you in the right folder? (`pwd` or `cd`)
2. Did you select the Python kernel? (bottom right in VS Code)
3. Are packages installed? (`pip list`)

**Try:**
```bash
cd example-project
conda activate base
jupyter notebook analysis.ipynb
```

### Getting Help

**When stuck:**
```bash
# Ask Claude!
claude chat "I got this error: [paste error]. How do I fix it?"
```

**That's literally the point of vibe coding!**

---

## 📊 Real-World Applications

### What You Can Build

**Quality Improvement:**
- Complication rate analysis
- Length of stay predictions
- Readmission risk models
- Process improvement metrics

**Research:**
- Outcome comparisons
- Risk factor identification
- Survival analysis
- Meta-analysis

**Education:**
- Case log analysis
- Resident performance tracking
- Teaching case databases
- Literature reviews

**All using this same workflow!**

---

## 🤝 Contributing

We welcome contributions! Whether it's:
- 🐛 Bug fixes
- 📝 Documentation improvements
- 💡 New examples
- 🎨 Better visualizations

**To contribute:**
1. Fork this repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

**TL;DR:** Use it freely, share it widely, modify as needed. Just keep the attribution

---

## 🎯 Success Metrics

**You've succeeded when you can:**

✅ Run the example and get results  
✅ Understand what each cell does  
✅ Modify colors, labels, and filters  
✅ Replace with your own data  
✅ Ask Claude for help effectively  
✅ Interpret statistical outputs  
✅ Use results in presentations/papers  

**You DON'T need to:**

❌ Memorize Python syntax  
❌ Debug complex errors alone  
❌ Become a software engineer  
❌ Spend months learning  

---

## 🚀 Next Steps

1. **⬇️ Clone or download this repository**
2. **▶️ Run the example** (5 minutes)
3. **📚 Read the guide** (1 hour)
4. **🔧 Adapt to your data** (30 minutes)
5. **📝 Publish your analysis!**
