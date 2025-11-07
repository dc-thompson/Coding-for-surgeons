# Vibe Coding for Surgeons: Start Analysing Data in 1 Hour

> **The Philosophy:** You don't need to be a programmer. You need to describe what you want, and AI (Claude) writes the code.

## What is Vibe Coding?

**Traditional Approach:**
1. Take Python course (40 hours)
2. Learn statistics libraries (20 hours)
3. Master data visualisation (10 hours)
4. Finally start your analysis

**Vibe Coding Approach:**
1. Install 3 things (15 minutes)
2. Tell Claude what you want (5 minutes)
3. Claude writes the code (instant)
4. You're analysing data! 

**The Key Insight:** Modern AI (like Claude) can write code. You just need to know:
- What's possible
- How to ask for it clearly
- How to verify it makes sense

Think of it like using the da Vinci robot. You don't need to know how to build it, just how to operate it.

---

## What You'll Learn

By the end of this guide (60 minutes total), you'll be able to:

✅ Set up a coding environment  
✅ Load your surgical data (CSV, Excel, whatever)  
✅ Ask Claude to analyze it  
✅ Generate statistics, graphs, and tables  
✅ Save results for your paper/presentation

**No memorization required.** If you forget something, just ask Claude again.

---

## Prerequisites

- **A computer** (Windows or Mac)
- **Your data** (Excel, CSV, or similar)
- **A question** ("What's my complication rate by procedure?")
- **30-60 minutes of time**

That's literally it.

---

## The 4-Step Quick Start

### **Step 1: Quick Setup (15 min)**
Install Anaconda, VS Code, and Claude Code.  
→ **[Go to Quick Setup Guide](docs/quick-setup.md)**

### **Step 2: Your First Project (10 min)**
Copy our project template and open it in VS Code.  
→ **[Go to First Project Guide](docs/first-project.md)**

### **Step 3: Talking to Claude (10 min)**
Learn how to ask Claude to write code for you.  
→ **[Go to Talking to Claude Guide](docs/talking-to-claude.md)**

### **Step 4: Complete Example (25 min)**
Follow along with a real complication rate analysis.  
→ **[Go to Example Analysis](docs/example-analysis.md)**

---

## What Makes This Different?

**Other coding guides:**
- Teach you syntax (boring!)
- Make you memorize functions (unnecessary!)
- Assume you want to be a programmer (you don't!)

**This guide:**
- Shows you how to use AI to code
- Focuses on YOUR data and YOUR questions
- Gets you results fast
- Teaches just enough to be dangerous

---

## A Note on Safety ⚠️

**Claude is powerful but not infallible.**

Think of Claude like an enthusiastic intern:
- ✅ Fast and knowledgeable
- ✅ Handles tedious work
- ✅ Rarely makes obvious mistakes
- ❌ But YOU need to review everything
- ❌ YOU are responsible for the results

**Always verify:**
- Sample sizes make sense
- Statistics are appropriate
- Graphs match your data
- Results align with clinical reality

**Review everything.** 

---

## What You'll Build

By following this guide, you'll create:

```
my_surgical_analysis/
│
├── data/
│   └── surgical_data.csv         # Your data
│
├── analysis.ipynb                # Your analysis (with Claude's help)
│
├── results/
│   ├── complication_rates.csv    # Generated tables
│   └── figures/                  # Generated graphs
│       ├── rates_by_procedure.png
│       └── risk_factors.png
│
└── README.md                     # What this project does
```

---

## Real Examples of What You Can Do

**With 10 minutes and Claude's help:**

**"Load my surgical outcomes data and show me complication rates by procedure"**
→ Claude writes code that loads your data, calculates rates, and creates a table

**"Make a bar chart of complication rates with 95% confidence intervals"**
→ Claude generates a publication-quality figure

**"Test if comorbidity count is associated with complications"**
→ Claude runs a logistic regression and explains the results

**"Export these results to a table I can paste into my paper"**
→ Claude formats everything for Word/LaTeX

---

### "How much does this cost?"

- **Anaconda:** Free
- **VS Code:** Free
- **Claude Code:** Requires Claude Pro ($20/month)

Worth it to save 100+ hours learning to code the traditional way.

### "What if I need help?"

1. Ask Claude! (Seriously, Claude can debug its own code)
2. Google the error message
3. Ask a colleague who codes

Most issues are solved in 5 minutes.

### "Will this work with my data?"

If you can open your data in Excel, Claude can analyze it.

Common formats that work:
- CSV files (.csv)
- Excel files (.xlsx, .xls)
- Text files (.txt)
- SPSS files (.sav)
- Stata files (.dta)

### "Is this patient data compliant?"

**CRITICAL SAFETY WARNING:**

- ⚠️ **DO NOT** upload identifiable patient data to Claude
- ✅ **DO** de-identify your data first
- ✅ **DO** use patient IDs instead of names/MRNs
- ✅ **DO** remove dates of birth, exact dates (use relative times)
- ✅ **DO** check your institution's data policy

When in doubt, err on the side of caution and consult your data lead.

---

## Let's Get Started

**Ready?** Let's install the tools and start analyzing your data.

→ **[Go to Quick Setup Guide](docs/quick-setup.md)** (15 minutes)

---
