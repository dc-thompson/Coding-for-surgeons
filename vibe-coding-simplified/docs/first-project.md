# Your First Project: Set Up in 10 Minutes

> **Goal:** Create a project folder and start analyzing your data  
> **Time:** 10 minutes

## The Project Template

Every analysis project has the same basic structure:

```
my_surgical_analysis/
│
├── data/                  # Your raw data (CSV, Excel, etc.)
│   └── .gitkeep          # Keeps folder in git
│
├── analysis.ipynb        # Your Jupyter notebook (where the magic happens)
│
├── results/              # Generated outputs
│   ├── figures/          # Graphs and plots
│   └── tables/           # Statistical tables
│
└── README.md             # What this project does
```

**Surgical analogy:** Think of this like organizing your OR:
- `data/` = Patient records (raw materials)
- `analysis.ipynb` = Your operative note (the work)
- `results/` = Your dictation and photos (final outputs)

---

## Method 1: Let Claude Create It (Easiest!)

**1. Decide where to put your project:**

Pick a location. I recommend your Desktop or Documents folder:

```bash
# Mac
cd ~/Desktop

# Windows
cd %USERPROFILE%\Desktop
```

**2. Ask Claude to create the project:**

```bash
claude chat "Create a project folder called 'complication_analysis' with subfolders for data, results, and results/figures. Also create a blank Jupyter notebook called analysis.ipynb and a README.md file explaining this is a surgical complication rate analysis project."
```

**3. Open it in VS Code:**

```bash
cd complication_analysis
code .
```

**Done!** Claude just built your entire project structure. ✅

---

## Method 2: Create It Manually (If You Prefer)

**1. Create the main folder:**

```bash
# Mac/Linux
mkdir ~/Desktop/my_analysis
cd ~/Desktop/my_analysis

# Windows
mkdir %USERPROFILE%\Desktop\my_analysis
cd %USERPROFILE%\Desktop\my_analysis
```

**2. Create subfolders:**

```bash
mkdir data
mkdir results
mkdir results/figures
mkdir results/tables
```

**3. Create your notebook:**

Open VS Code:
```bash
code .
```

In VS Code:
- Press `Ctrl/Cmd + N` (new file)
- Press `Ctrl/Cmd + S` (save)
- Name it: `analysis.ipynb`
- VS Code will recognize it's a Jupyter notebook

**4. Create README:**

- Press `Ctrl/Cmd + N` again
- Press `Ctrl/Cmd + S`
- Name it: `README.md`
- Add this text:

```markdown
# My Surgical Analysis

## Purpose
Analysis of [describe your data]

## Data
- Source: [where did you get it]
- Time period: [when]
- Sample size: [how many cases]

## Questions
1. What is the complication rate by procedure?
2. What factors predict complications?

## Status
- [ ] Data loaded
- [ ] Initial exploration
- [ ] Statistical analysis
- [ ] Visualization
- [ ] Results written up
```

---

## Project Structure Explained

### `data/` folder

**What goes here:** Your original, unmodified data files.

**Never modify files in this folder!** Always keep your raw data pristine.

Common file types:
- `surgical_data.csv` - From Excel or database
- `outcomes.xlsx` - Excel file
- `patient_list.txt` - Text file

**HIPAA warning:** ⚠️ Make sure data is de-identified before putting it here!

### `analysis.ipynb` file

This is your Jupyter notebook - where you'll do all your work.

**What's a Jupyter notebook?**
- Think of it like a lab notebook for code
- Mix code, results, and notes all in one place
- Run code in chunks ("cells")
- See results immediately
- Can export to HTML or PDF when done

**Why use notebooks?**
- Easy to experiment and iterate
- See your results as you go
- Great for exploration and one-off analyses
- Can share with collaborators who can see everything

### `results/` folder

**What goes here:** Everything your analysis generates.

```
results/
├── figures/
│   ├── complication_rates.png
│   ├── risk_factors.png
│   └── kaplan_meier.png
│
└── tables/
    ├── descriptive_stats.csv
    ├── regression_results.csv
    └── complications_by_procedure.csv
```

These files are **generated** by your analysis - you can always recreate them.

### `README.md` file

**What is it:** A description of your project in plain text.

**Why have one:**
- Reminds you what this project is about (6 months later!)
- Tells collaborators what you're doing
- Documents your analysis approach

**Pro tip:** Update it as you go. Future you will thank present you!

---

## Adding Your Data

**1. Save your data file to the `data/` folder**

Options:
- Drag and drop the file into VS Code
- Copy it manually using File Explorer/Finder
- Use terminal:

```bash
# Mac
cp ~/Downloads/my_data.csv data/

# Windows
copy %USERPROFILE%\Downloads\my_data.csv data\
```

**2. Verify it's there:**

In VS Code, you should see it in the file explorer on the left.

---

## Opening Your Notebook

**1. In VS Code, click on `analysis.ipynb`**

**2. Select kernel:**

VS Code will ask "Select Kernel" - choose:
- Python 3.x (whatever version you have)
- Should say "conda" or "anaconda"

**3. You're ready to code!**

You should see:
- An empty cell at the top
- Buttons to run code
- Output area below each cell

---

## Your First Cell

Let's test everything works. In the first cell, type:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

print("✅ Everything works!")
print(f"Pandas version: {pd.__version__}")
print(f"NumPy version: {np.__version__}")
```

**Click the play button (▶️) or press `Shift + Enter`**

You should see:
```
✅ Everything works!
Pandas version: 2.0.3
NumPy version: 1.24.3
```

**If you see that, you're ready to analyze data!** ✅

**If you see an error:**
- Make sure you selected the right kernel (Python with conda)
- Restart the kernel: Click the ↻ icon at the top
- Try again

---

## Next Steps

Now you're set up! Time to learn how to ask Claude to help with your analysis.

→ **[Next: Talking to Claude](talking-to-claude.md)**

---

## Quick Tips

### Jupyter Notebook Shortcuts

**Running cells:**
- `Shift + Enter` - Run cell and move to next
- `Ctrl/Cmd + Enter` - Run cell and stay on it
- Click ▶️ button

**Adding cells:**
- `A` - Add cell above (might not work in VS Code, just click the + button)
- `B` - Add cell below
- Click `+ Code` button

**Other useful:**
- `DD` - Delete cell (press D twice)
- `Z` - Undo cell deletion
- Click `...` for more options

### Saving Your Work

**Auto-save is ON by default** in VS Code, but you can manually save:
- `Ctrl/Cmd + S`

Your notebook saves the code AND the outputs, so when you reopen it, you can see your previous results.

### Restarting When Things Break

**If your code gets stuck or errors keep happening:**

1. Click the ↻ (restart kernel) button at the top
2. This clears everything and starts fresh
3. Re-run your cells from the top

Think of it like rebooting the computer - solves most problems!

---

## Project Template for Different Analyses

You can copy this structure for any project:

**For complication analysis:**
```
complication_analysis/
├── data/
├── analysis.ipynb
└── results/
```

**For survival analysis:**
```
survival_analysis/
├── data/
├── analysis.ipynb
└── results/
```

**For literature review:**
```
literature_review/
├── data/
│   └── pubmed_results.csv
├── analysis.ipynb
└── results/
```

Same structure, different content. Simple!

---

## What If I Want to Use Git?

**Git = Time machine for your code.** Every save becomes a checkpoint you can return to.

**To initialize git in your project:**

```bash
cd my_analysis
git init
```

**To save a checkpoint:**

```bash
git add .
git commit -m "Initial analysis setup"
```

**Not necessary for beginners!** You can add this later when you're comfortable.

---

**You now have a project!** Time to learn how to talk to Claude and start analyzing.

→ **[Next: Talking to Claude](talking-to-claude.md)**
