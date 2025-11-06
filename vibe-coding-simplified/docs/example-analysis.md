# Complete Example: Analyzing Surgical Complication Rates

> **Goal:** Walk through a complete analysis from raw data to publication-ready results  
> **Time:** 25-30 minutes  
> **What you'll learn:** The entire vibe coding workflow with Claude

## The Scenario

You're analyzing complication rates from your surgical service. You have:

**Data:** 500 surgical cases from the past year  
**Question:** What are the complication rates by procedure type?  
**Goal:** Create a table and figure for your QI presentation

Let's build this together using Claude!

---

## Step 1: Set Up the Project (3 minutes)

**1. Create project folder:**

```bash
cd ~/Desktop
mkdir complication_analysis
cd complication_analysis
```

**2. Ask Claude to set up the structure:**

```bash
claude chat "Create project folders for data, results, and results/figures. Create a Jupyter notebook called analysis.ipynb and a README.md explaining this is a surgical complication rate analysis."
```

Claude creates everything!

**3. Open in VS Code:**

```bash
code .
```

---

## Step 2: Prepare Your Data (5 minutes)

**For this example, let's create sample data.**

Create a new file called `generate_sample_data.py`:

```bash
claude edit generate_sample_data.py "Create a Python script that generates realistic sample surgical data with 500 rows. Include columns: patient_id (integers 1-500), procedure (choose randomly from: Appendectomy, Cholecystectomy, Hernia Repair, Colectomy), age (random 20-80), asa_class (1-4), comorbidity_count (0-5), complication (0 or 1, with higher rates for higher ASA class). Save as data/surgical_data.csv"
```

Claude creates the script. Now run it:

```bash
python generate_sample_data.py
```

You should see: `data/surgical_data.csv` created!

**For real analysis:** Just copy your actual de-identified CSV to the `data/` folder instead.

---

## Step 3: Initial Data Exploration (5 minutes)

**Open `analysis.ipynb` in VS Code.**

**Ask Claude to start your analysis:**

```bash
claude edit analysis.ipynb "Create the first few cells of a Jupyter notebook that:
1. Imports pandas, numpy, matplotlib, seaborn
2. Loads data/surgical_data.csv
3. Displays first 5 rows
4. Shows data info (dtypes, missing values)
5. Displays summary statistics
6. Adds markdown cells explaining each step"
```

**Run the notebook!**

Click the ▶️ button on each cell (or Shift+Enter).

You should see:
- Your data loaded ✅
- First few rows displayed ✅
- Data types and summary stats ✅

**Take a moment to review the output.**

Does the data look reasonable?
- Correct number of rows? ✅
- Expected column names? ✅
- Any missing values? (Check this!)
- Do the values make sense clinically? ✅

---

## Step 4: Calculate Complication Rates (7 minutes)

**Now ask Claude for the actual analysis:**

```bash
claude chat "I need to calculate complication rates by procedure with 95% confidence intervals. My data has columns: patient_id, procedure, age, asa_class, comorbidity_count, complication (0/1). What's the best approach for confidence intervals with small sample sizes?"
```

Claude will explain Wilson score intervals are best for small samples!

**Then create the analysis function:**

```bash
claude edit analysis.ipynb "Add cells that:
1. Create a function calculate_complication_rates(df) that:
   - Groups by procedure
   - Counts total cases and complications for each
   - Calculates rate as complications/total
   - Uses Wilson score method for 95% CI
   - Returns a DataFrame with columns: procedure, n_cases, n_complications, rate, ci_lower, ci_upper
2. Call this function and display the results table
3. Add markdown explaining what Wilson score intervals are and why we use them"
```

**Run these new cells!**

You should see a nice table like:

```
procedure          n_cases  n_complications  rate   ci_lower  ci_upper
Appendectomy       125      8               0.064  0.032     0.121
Cholecystectomy    132      15              0.114  0.068     0.179
Colectomy          118      22              0.186  0.125     0.267
Hernia Repair      125      6               0.048  0.022     0.100
```

**Clinical sense check:**
- Do these rates seem reasonable? ✅
- Are higher-risk procedures showing higher rates? ✅
- Do confidence intervals overlap appropriately? ✅

---

## Step 5: Visualize the Results (5 minutes)

**Ask Claude to create a publication-quality figure:**

```bash
claude edit analysis.ipynb "Add cells that create a bar chart showing:
- Complication rates by procedure on y-axis
- Procedure names on x-axis
- Error bars showing 95% CI
- Professional styling suitable for presentation
- Save figure as results/figures/complication_rates.png at 300 DPI
Add markdown explaining how to interpret the figure"
```

**Run the cells!**

You should see a beautiful bar chart with error bars.

**Review the figure:**
- Are procedures in a logical order? (Maybe alphabetical or by rate?)
- Are error bars visible and clear? ✅
- Is text readable? ✅
- Would this look good in a PowerPoint? ✅

**If you want changes:**

```bash
claude edit analysis.ipynb "Make the figure wider, sort procedures by complication rate (highest to lowest), and use a color gradient from green (low) to red (high)"
```

Claude modifies it immediately!

---

## Step 6: Statistical Testing (5 minutes)

**Let's test if complication rates differ by procedure:**

```bash
claude chat "I want to test if complication rates differ significantly between procedures. What statistical test should I use and how do I implement it?"
```

Claude will suggest Chi-square test and provide code!

**Add it to your notebook:**

```bash
claude edit analysis.ipynb "Add cells that:
1. Perform Chi-square test comparing complication rates across procedures
2. Display the test statistic, p-value, and interpretation
3. Add markdown explaining what this test tells us
4. If significant, add post-hoc pairwise comparisons with Bonferroni correction"
```

**Run it!**

You might see:
```
Chi-square test: χ² = 18.42, p = 0.0004

Complication rates differ significantly between procedures.

Pairwise comparisons:
Colectomy vs Hernia Repair: p = 0.001 ***
Colectomy vs Appendectomy: p = 0.012 *
...
```

**Clinical interpretation:**

Higher-risk procedures (Colectomy) have significantly higher complication rates than lower-risk procedures (Hernia Repair). Makes sense!

---

## Step 7: Risk Factor Analysis (5 minutes)

**Let's check if patient factors predict complications:**

```bash
claude edit analysis.ipynb "Add cells that:
1. Perform logistic regression with complication as outcome
2. Predictors: age, asa_class, comorbidity_count, and procedure type
3. Display odds ratios with 95% CI
4. Create a forest plot of the odds ratios
5. Add interpretation of which factors significantly predict complications"
```

**Run it!**

You'll get output like:

```
Logistic Regression Results:

Variable              Odds Ratio  95% CI         p-value
Age (per year)        1.02        [0.99, 1.04]   0.156
ASA Class (per unit)  2.15        [1.56, 2.98]   <0.001 ***
Comorbidities         1.18        [1.03, 1.35]   0.021 *
Procedure:
  Colectomy (ref)     1.00        -              -
  Appendectomy        0.28        [0.12, 0.62]   0.002 **
  Cholecystectomy     0.54        [0.27, 1.08]   0.082
  Hernia Repair       0.21        [0.08, 0.53]   0.001 **
```

**Clinical takeaway:**
- ASA class is the strongest predictor (2.15× risk per class)
- Comorbidity count matters but less so
- Age doesn't significantly predict complications in this cohort
- Procedure type matters even after adjusting for patient factors

---

## Step 8: Export Results (3 minutes)

**Save your tables for the paper:**

```bash
claude edit analysis.ipynb "Add cells that:
1. Export the complication rates table to results/tables/rates_by_procedure.csv
2. Export the logistic regression results to results/tables/risk_factors.csv
3. Format both tables with appropriate decimal places
4. Add a final markdown cell summarizing what was saved and where"
```

**Run it!**

Check your `results/` folder:
- ✅ `figures/complication_rates.png` - Ready for PowerPoint
- ✅ `tables/rates_by_procedure.csv` - Ready for Excel/Word
- ✅ `tables/risk_factors.csv` - Ready for manuscript

---

## Step 9: Document Everything (2 minutes)

**Update your README:**

```bash
claude edit README.md "Write a comprehensive README that includes:
- Project title and purpose
- Data description (n=500 surgical cases)
- Key findings from the analysis
- File structure explanation
- How to reproduce the analysis
- Requirements (pandas, numpy, scipy, matplotlib, seaborn, scikit-learn)
- Author and date"
```

**Perfect!** Now if you (or someone else) opens this project in 6 months, they'll understand everything.

---

## Step 10: Review and Iterate (Ongoing)

**Your analysis is done! But vibe coding makes iteration easy.**

Want to add something? Just ask Claude:

```bash
# Add a survival analysis
claude chat "How would I add Kaplan-Meier curves for time to complication?"

# Create different visualizations
claude chat "Can you show me 3 alternative ways to visualize these complication rates?"

# Add more sophisticated analysis
claude chat "Should I adjust for confounders differently? What about propensity score matching?"

# Improve the code
claude edit analysis.ipynb "Add detailed comments explaining each step for a colleague who's new to Python"
```

---

## The Complete Workflow Summary

**What we just did in 30 minutes:**

1. ✅ Set up professional project structure
2. ✅ Generated/loaded surgical data
3. ✅ Explored and validated data
4. ✅ Calculated complication rates with confidence intervals
5. ✅ Created publication-quality visualization
6. ✅ Performed statistical testing (Chi-square)
7. ✅ Built logistic regression model
8. ✅ Generated forest plot of risk factors
9. ✅ Exported all results
10. ✅ Documented everything

**Without Claude, this would take:** 4-8 hours (if you know how to code)  
**With Claude:** 30 minutes ⚡

**That's the power of vibe coding!**

---

## Key Lessons from This Example

### 1. Start Simple, Build Complexity

We didn't try to do everything at once:
- First: Load data
- Then: Basic calculations
- Then: Visualization
- Then: Statistical testing
- Then: Advanced modeling
- Finally: Export and document

### 2. Ask Claude for Advice

We asked Claude:
- "What's the best CI method for small samples?" (Wilson score)
- "What statistical test?" (Chi-square)
- "How to handle multiple comparisons?" (Bonferroni)

### 3. Review Everything

After each step, we:
- Ran the code
- Looked at outputs
- Checked if results made clinical sense
- Iterated if needed

### 4. Use Markdown for Context

Our notebook mixed:
- Code cells (what we're doing)
- Markdown cells (why we're doing it)

Future you will appreciate the explanations!

### 5. Save Everything Systematically

All outputs went to `results/`:
- Raw tables → `tables/`
- Figures → `figures/`

Easy to find everything later!

---

## Adapting This to Your Data

**To use this workflow with your own data:**

1. **Replace Step 2:** Skip `generate_sample_data.py`, use your real CSV

2. **Adjust column names:** Tell Claude your actual column names:
   ```bash
   claude edit analysis.ipynb "My data has columns: MRN, procedure_name, patient_age, complication_yn. Update all code to use these column names."
   ```

3. **Modify analyses:** Ask for what you need:
   ```bash
   claude chat "Instead of procedure type, I want to analyze by surgeon. How do I modify the analysis?"
   ```

4. **Different visualizations:** 
   ```bash
   claude chat "I need this as a forest plot instead of a bar chart"
   ```

**Claude adapts to YOUR needs!**

---

## Common Variations

### For Survival Analysis:

```bash
claude chat "I have time-to-event data (days until complication). How do I do Kaplan-Meier analysis and Cox regression?"
```

### For Longitudinal Data:

```bash
claude chat "My data has multiple visits per patient. How do I analyze repeated measures?"
```

### For Meta-Analysis:

```bash
claude chat "I have effect sizes from 15 different studies. How do I perform meta-analysis and create a forest plot?"
```

### For Predictive Modeling:

```bash
claude chat "I want to build a model to predict who will have complications. Should I use logistic regression, random forest, or something else?"
```

**Claude can help with all of these!**

---

## Troubleshooting This Example

### "My data won't load"

**Check:**
- Is the file in the `data/` folder?
- Is the filename exactly right (case-sensitive on Mac)?
- Does the file open in Excel?

**Ask Claude:**
```bash
claude chat "I'm getting FileNotFoundError when loading my CSV. Here's my code: [paste]. The file is definitely in data/ folder. What's wrong?"
```

### "I get errors when running cells"

**Check:**
- Did you install all packages? (`pip install pandas numpy scipy matplotlib seaborn scikit-learn`)
- Did you run cells in order?
- Did you select the right kernel?

**Ask Claude:**
```bash
claude chat "I get this error: [paste error]. Here's my code: [paste code]. How do I fix it?"
```

### "Results don't make sense"

**Check:**
- Do your rates match manual calculations?
- Are confidence intervals reasonable?
- Do statistical tests make clinical sense?

**Ask Claude:**
```bash
claude chat "My complication rate is 200%. That can't be right. Here's my data and code: [paste]. What's wrong?"
```

### "Figures look bad"

**Ask Claude to improve:**
```bash
claude edit analysis.ipynb "The text on my figure is too small and overlaps. Make it larger and rotate x-axis labels."
```

---

## Next Steps

**You just completed a full analysis!** 🎉

### What to do now:

**1. Try with your own data**
- Follow the same steps
- Adapt prompts to your column names
- Ask Claude when stuck

**2. Experiment**
- Try different visualizations
- Add more analyses
- Learn by doing

**3. Share your work**
- Show colleagues
- Present results
- Publish papers

**4. Keep learning**
- Each project teaches you more
- Build a library of prompts that work
- Help others get started

---

## Resources for Going Further

### When You Want to Learn More:

**Ask Claude for recommendations:**
```bash
claude chat "I want to learn more about statistical analysis in Python. What resources do you recommend for a surgeon?"
```

**Try more complex projects:**
- Meta-analyses
- Machine learning models
- Interactive dashboards
- Automated reports

**Join communities:**
- Python for surgeons (if exists!)
- Data science communities
- Stack Overflow (for specific questions)

### When You Need Traditional Learning:

**Sometimes you want to understand deeply:**
- Take a formal Python course (Coursera, DataCamp)
- Read "Python for Data Analysis" by Wes McKinney
- Work through statistics tutorials

**But remember:** You don't need to master everything before being productive!

---

## Final Thoughts

**Traditional Coding Path:**
- Months of learning
- Frustration and debugging
- Finally productive

**Vibe Coding Path:**
- Productive immediately
- Learn while doing
- AI handles the details

**You just proved it works.** In 30 minutes, you went from nothing to a complete analysis with:
- Statistical testing ✅
- Logistic regression ✅
- Publication-quality figures ✅
- Exportable results ✅

**That's the future of research computing for busy clinicians.**

---

## Your Turn

**Clone this example and modify it for your needs:**

1. Get your de-identified data
2. Set up a project (like we did)
3. Ask Claude to help analyze it
4. Iterate until you have results
5. Share with your colleagues

**You're now a vibe coder!** 🎉

---

## Quick Reference: Commands We Used

```bash
# Project setup
mkdir project_name
cd project_name
code .

# Claude commands
claude chat "question or request"
claude edit filename "modification"

# Jupyter operations
# (In VS Code: Click ▶️ or Shift+Enter)

# Export results
df.to_csv('results/tables/output.csv')
fig.savefig('results/figures/plot.png', dpi=300)
```

---

**Questions? Ask Claude!**

```bash
claude chat "I finished the example but want to [your goal]. How do I do that?"
```

That's vibe coding. When in doubt, ask Claude. 🤖

**Now go analyze some data!** 🚀
