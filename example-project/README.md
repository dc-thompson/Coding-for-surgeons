# Surgical Complication Analysis - Example Project

## 🎯 What is This?

This is a **complete, ready-to-run example** of a surgical data analysis using Python and Jupyter notebooks. You can run it right now to see results, then adapt it for your own data.

**Time to results:** 5-10 minutes ⚡

---

## 📁 Project Structure

```
example-project/
│
├── README.md                           # This file
├── analysis.ipynb                      # Jupyter notebook (run this!)
│
├── data/
│   └── surgical_data.csv              # Sample data (120 cases)
│
└── results/                           # Generated outputs appear here
    ├── figures/
    │   ├── complication_rates.png
    │   └── forest_plot.png
    └── tables/
        ├── complication_rates.csv
        └── risk_factors.csv
```

---

## 🚀 Quick Start (5 Minutes)

### 1. Open the Notebook

**In VS Code:**
```bash
cd example-project
code .
```

Then click on `analysis.ipynb`

**Or in Jupyter:**
```bash
cd example-project
jupyter notebook analysis.ipynb
```

### 2. Run All Cells

- **In VS Code:** Click "Run All" at the top
- **In Jupyter:** Menu → Cell → Run All
- **Keyboard shortcut:** Press `Shift + Enter` on each cell

### 3. Check Results

Look in the `results/` folder for:
- Bar chart of complication rates
- Forest plot of risk factors
- CSV tables ready for your paper

**That's it!** You just completed a full analysis. 🎉

---

## 📊 What This Analysis Does

### Data

**120 surgical cases** with:
- 4 procedure types (Appendectomy, Cholecystectomy, Colectomy, Hernia Repair)
- Patient demographics (age, sex)
- Risk factors (ASA class, comorbidities, BMI)
- Outcomes (complications, length of stay)

### Analyses

1. **Descriptive statistics** - Summary of the data
2. **Complication rates by procedure** - With 95% confidence intervals
3. **Chi-square test** - Do rates differ significantly?
4. **Logistic regression** - What predicts complications?
5. **Visualizations** - Publication-quality figures

### Outputs

✅ **Tables** (CSV format - paste into Excel/Word)
- Complication rates by procedure
- Logistic regression results

✅ **Figures** (PNG format at 300 DPI - ready for presentations)
- Bar chart with error bars
- Forest plot of risk factors

---

## 🔧 Adapting This to Your Data

### Option A: Replace the CSV File

1. **Save your data** as `data/my_surgical_data.csv`
2. **Update the file path** in the notebook (Cell under "Step 2"):
   ```python
   df = pd.read_csv('data/my_surgical_data.csv')  # Change this line
   ```
3. **Run the notebook** again

### Option B: Ask Claude to Modify

If your data has different columns, ask Claude:

```bash
claude edit analysis.ipynb "My data has columns: patient_number, operation_type, complication_yes_no. Update the code to use these column names."
```

Claude will modify the entire notebook for you!

### Option C: Clone and Customize

1. **Copy this folder:**
   ```bash
   cp -r example-project my-actual-analysis
   cd my-actual-analysis
   ```

2. **Replace the data file**

3. **Run and iterate**

---

## 💡 Common Modifications

### Add More Visualizations

```bash
claude chat "How do I add a Kaplan-Meier survival curve to this analysis?"
```

### Change Statistical Tests

```bash
claude chat "Should I use Mann-Whitney instead of t-test for this data?"
```

### Add Subgroup Analyses

```bash
claude edit analysis.ipynb "Add a section that analyzes complications separately for males and females"
```

### Export to Different Format

```bash
claude chat "How do I export this notebook as a PDF report?"
```

---

## 📖 Learning from This Example

### What to Notice

**Good practices in this notebook:**
- ✅ Markdown cells explain each step
- ✅ Code is well-commented
- ✅ Results are saved automatically
- ✅ Visualizations are publication-quality
- ✅ Statistical methods are appropriate

**Structure:**
1. Import libraries
2. Load data
3. Explore data
4. Analyze
5. Visualize
6. Export results

**Copy this structure for your own projects!**

### What to Change

**For your analysis, you'll likely need to:**
- Change file paths
- Update column names
- Modify statistical tests
- Adjust visualizations
- Add your own analyses

**Just ask Claude for help with any of these!**

---

## 🔍 Detailed Walkthrough

### Cell 1: Import Libraries

**What it does:** Loads the tools we need (pandas, numpy, scipy, matplotlib)

**When to modify:** Rarely. These are the standard libraries.

**If you get errors:** 
```bash
pip install pandas numpy scipy statsmodels matplotlib seaborn --break-system-packages
```

---

### Cell 2-4: Load and Explore Data

**What it does:** Reads CSV, shows first rows, checks for missing data

**When to modify:** Update the file path if using your own data

**Key checks:**
- Does the data load without errors?
- Are the column names correct?
- Any missing values?
- Do the numbers look reasonable?

---

### Cell 5: Calculate Rates

**What it does:** Computes complication rates by procedure with confidence intervals

**Why Wilson score?** Best method for proportions, especially with small sample sizes

**When to modify:** If you want rates by different groups (e.g., by surgeon, by year)

---

### Cell 6: Visualize Rates

**What it does:** Creates a bar chart with error bars

**When to modify:** 
- Change colors: `color='steelblue'` → `color='red'`
- Sort differently: `ascending=False` → `ascending=True`
- Change figure size: `figsize=(10, 6)` → `figsize=(12, 8)`

---

### Cell 7-8: Statistical Testing

**What it does:** Chi-square test to compare procedures

**When to modify:** 
- If you have continuous outcomes, use ANOVA
- If you have paired data, use McNemar's test
- Ask Claude: "What test should I use for my data?"

---

### Cell 9-10: Logistic Regression

**What it does:** Identifies risk factors that predict complications

**When to modify:**
- Add/remove predictors
- Change reference category
- Add interaction terms

**Ask Claude:** "How do I add interaction between ASA class and age?"

---

### Cell 11: Forest Plot

**What it does:** Visualizes odds ratios from regression

**When to modify:** Colors, size, labels

---

### Cell 12: Export Results

**What it does:** Saves tables as CSV files

**When to modify:** 
- Different format: `.to_csv()` → `.to_excel()`
- Different location: `'results/tables/'` → `'outputs/'`

---

## ⚠️ Important Reminders

### Data Privacy

**Before using your real data:**
- ✅ De-identify all patient information
- ✅ Remove names, MRNs, dates of birth
- ✅ Use relative dates if needed
- ✅ Check your institution's data policies

**Never upload** identifiable data to Claude!

### Code Review

**Always review the code:**
- Does the logic make sense?
- Are the statistical methods appropriate?
- Do results align with clinical expectations?

**You're the attending, Claude is the resident!**

### Version Control

**Good practice:**
```bash
git init
git add .
git commit -m "Initial analysis"
```

Save checkpoints as you go!

---

## 🆘 Troubleshooting

### "ModuleNotFoundError: No module named 'pandas'"

**Fix:**
```bash
pip install pandas numpy scipy statsmodels matplotlib seaborn --break-system-packages
```

### "FileNotFoundError: data/surgical_data.csv"

**Fix:** Make sure you're in the right folder:
```bash
pwd  # Should show .../example-project
ls data/  # Should show surgical_data.csv
```

### Cells Won't Run

**Fix:**
1. Restart kernel (click ↻ icon)
2. Check you selected the right Python interpreter
3. Run cells in order from top to bottom

### Results Look Wrong

**Fix:**
1. Check data loaded correctly: `print(df.head())`
2. Verify column names: `print(df.columns)`
3. Look for missing data: `print(df.isnull().sum())`
4. Ask Claude: "My rates are over 100%, what's wrong?"

---

## 📚 Next Steps

### After Running This Example:

1. **Understand the flow** - Read through each cell
2. **Modify something small** - Change a color, add a filter
3. **Run it again** - See your changes
4. **Try your own data** - Start small, one analysis at a time
5. **Ask Claude for help** - When you get stuck

### Build Your Own Project:

```bash
# Copy this structure
mkdir my-qI-project
cd my-qi-project
mkdir data results results/figures results/tables

# Copy the notebook as a template
cp ../example-project/analysis.ipynb .

# Modify for your needs
claude edit analysis.ipynb "Update this for cholecystectomy outcomes"
```

---

## 🎓 What You Learned

By running this example, you've seen:

✅ How to structure a data analysis project  
✅ How to load and explore data  
✅ How to calculate rates and confidence intervals  
✅ How to perform statistical tests  
✅ How to create publication-quality figures  
✅ How to export results  

**And you did it in 5-10 minutes!** That's the power of having a working template.

---

## 💬 Getting Help

### In This Notebook

Every cell has comments explaining what it does. Read them!

### Ask Claude

```bash
# General questions
claude chat "Explain what Wilson score intervals are"

# Specific modifications
claude edit analysis.ipynb "Add a section calculating median length of stay by procedure"

# Debugging
claude chat "I got this error: [paste error]. How do I fix it?"
```

### Online Resources

- **Stack Overflow** - For specific error messages
- **pandas documentation** - For data manipulation
- **seaborn gallery** - For visualization examples

---

## 🎉 Congratulations!

You now have a **complete working example** of a surgical data analysis.

**Next steps:**
1. Run it to see it work
2. Modify it gradually
3. Apply it to your data
4. Build your own analyses

**Remember:** You don't need to memorize any of this. Just run the notebook, see what it does, and ask Claude when you want to change something!

---

**Questions?** Ask Claude:

```bash
claude chat "I'm looking at the example notebook. How do I [what you want to do]?"
```

**Ready to analyze your own data?** Just replace the CSV file and run it again! 🚀
