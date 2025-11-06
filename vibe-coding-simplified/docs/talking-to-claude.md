# Talking to Claude: How to Ask for What You Want

> **Goal:** Learn to communicate with Claude effectively  
> **Time:** 10 minutes to read, lifetime to master

## The Core Principle

**Claude is your surgical resident.**

Good residents need:
- ✅ Clear instructions
- ✅ Relevant context
- ✅ Specific goals
- ✅ Permission to ask clarifying questions

Bad residents get:
- ❌ Vague requests ("Do something with this data")
- ❌ No context ("Figure it out")
- ❌ Contradictory instructions

Same with Claude.

---

## Two Ways to Use Claude Code

### Method 1: Chat Mode (For Questions and Planning)

**When to use:**
- Asking how to approach something
- Getting explanations
- Debugging errors
- Planning your analysis

**How to use:**

```bash
claude chat "Your question or request here"
```

**Examples:**

```bash
# Ask a question
claude chat "What's the best way to calculate 95% confidence intervals for proportions?"

# Get help with an error
claude chat "I got this error: KeyError: 'procedure'. What does this mean?"

# Plan an analysis
claude chat "I have surgical data with complications. How should I analyze it?"

# Learn something new
claude chat "What's the difference between logistic and linear regression?"
```

**Pro tip:** Chat mode is great for thinking out loud and getting advice.

### Method 2: Edit Mode (For Writing/Modifying Code)

**When to use:**
- Creating new code files
- Modifying existing code
- Fixing bugs in your code
- Adding features

**How to use:**

```bash
claude edit filename "What you want to change"
```

**Examples:**

```bash
# Create a new file
claude edit analysis.py "Create a function that loads a CSV file and returns a pandas DataFrame"

# Modify existing code
claude edit analysis.py "Add error handling for missing files"

# Fix a specific issue
claude edit analysis.py "The calculate_rates function is returning NaN values - fix this"

# Add functionality
claude edit analysis.py "Add a parameter to filter by date range"
```

**Pro tip:** Edit mode modifies files directly. Make sure you're in the right folder!

---

## The Anatomy of a Good Prompt

### Bad Prompt ❌

```bash
claude chat "Help with my data"
```

**Why it's bad:**
- Too vague
- No context
- Claude has to guess what you want

### Good Prompt ✅

```bash
claude chat "I have a CSV file with surgical complications data including columns: patient_id, procedure, age, comorbidities, complication_occurred. I want to calculate the complication rate for each procedure type and generate a bar chart with 95% confidence intervals. What's the best approach?"
```

**Why it's good:**
- ✅ Describes your data structure
- ✅ States the goal clearly
- ✅ Mentions desired output
- ✅ Asks for guidance

---

## The CRISP Framework for Complex Requests

For bigger tasks, use this structure:

**C**ontext - What are you working with?  
**R**equirements - What must it do?  
**I**nputs - What data format?  
**S**pecifics - Edge cases, preferences  
**P**urpose - Why are you doing this?

### Example: CRISP in Action

**Instead of:**
```bash
claude edit analysis.py "Load the data"
```

**Use CRISP:**
```bash
claude edit analysis.py "
Context: I'm analyzing post-operative complications from a surgical database.

Requirements: Create a function called load_surgical_data that:
- Loads a CSV file
- Validates required columns exist (patient_id, procedure, complication)
- Removes duplicates
- Returns a pandas DataFrame

Inputs: CSV file path as string

Specifics: 
- If columns are missing, raise a clear error message
- Drop rows with missing patient_id
- Print a summary of how many rows were loaded

Purpose: This is the first step in my complication rate analysis.
"
```

**Claude will give you much better code!**

---

## Common Vibe Coding Scenarios

### Scenario 1: Loading Your Data

**You:** "I have an Excel file with surgical cases. How do I load it?"

**Claude's approach:**
```python
import pandas as pd

df = pd.read_excel('data/surgical_cases.xlsx')
print(df.head())
print(df.shape)
```

**Then you can ask:**
```bash
claude chat "The Excel file has multiple sheets. How do I specify which one?"
```

### Scenario 2: Calculating Statistics

**You:** "Calculate complication rate by procedure type with confidence intervals"

**Claude will ask clarifying questions or provide code like:**
```python
from scipy import stats

def calculate_complication_rates(df):
    results = []
    
    for procedure in df['procedure'].unique():
        subset = df[df['procedure'] == procedure]
        n = len(subset)
        complications = subset['complication'].sum()
        rate = complications / n
        
        # Wilson score interval for 95% CI
        ci_low, ci_high = stats.binomial.proportion_confint(
            complications, n, method='wilson'
        )
        
        results.append({
            'procedure': procedure,
            'n_cases': n,
            'complications': complications,
            'rate': rate,
            'ci_low': ci_low,
            'ci_high': ci_high
        })
    
    return pd.DataFrame(results)
```

**No need to memorize this!** Just ask Claude again next time.

### Scenario 3: Making Plots

**You:** "Create a bar chart of complication rates with error bars"

**Claude provides:**
```python
import matplotlib.pyplot as plt

def plot_complication_rates(results_df):
    fig, ax = plt.subplots(figsize=(10, 6))
    
    # Create bar chart
    ax.bar(results_df['procedure'], results_df['rate'])
    
    # Add error bars (using CI width)
    errors = [
        results_df['rate'] - results_df['ci_low'],
        results_df['ci_high'] - results_df['rate']
    ]
    ax.errorbar(
        results_df['procedure'], 
        results_df['rate'],
        yerr=errors,
        fmt='none',
        color='black',
        capsize=5
    )
    
    ax.set_xlabel('Procedure')
    ax.set_ylabel('Complication Rate')
    ax.set_title('Complication Rates by Procedure (with 95% CI)')
    plt.xticks(rotation=45, ha='right')
    plt.tight_layout()
    
    return fig
```

### Scenario 4: Debugging Errors

**Your code crashes with:**
```
KeyError: 'procedure_type'
```

**You ask:**
```bash
claude chat "I'm getting KeyError: 'procedure_type' when running my analysis. Here's my code: [paste code]"
```

**Claude responds:**
"This error means the column 'procedure_type' doesn't exist in your DataFrame. Check your column names with `df.columns`. You might have named it 'procedure' instead."

### Scenario 5: Iterating on Code

**First request:**
```bash
claude edit analysis.py "Create a function to load CSV data"
```

**Claude creates basic loading function.**

**Then you refine:**
```bash
claude edit analysis.py "Add parameter to skip rows with missing procedure names"
```

**Then add more:**
```bash
claude edit analysis.py "Also add validation that complication column only contains 0 or 1"
```

**Build complexity gradually!**

---

## Tips for Effective Prompts

### 1. Be Specific About Data Structure

**Bad:**
```bash
"Load my data"
```

**Good:**
```bash
"Load a CSV file with columns: patient_id (integer), procedure (string), age (integer), complication (0 or 1)"
```

### 2. Mention Your Goal

**Bad:**
```bash
"Make a plot"
```

**Good:**
```bash
"Create a bar chart showing complication rates by procedure, suitable for a presentation"
```

### 3. Ask for Explanations

```bash
claude chat "What does this code do?" 
[paste code]
```

Claude will explain it in plain English.

### 4. Request Best Practices

```bash
claude chat "What's the best way to handle missing data in a complication analysis?"
```

### 5. Iterate Don't Perfect

**Don't try to get perfect code in one prompt!**

Start simple:
1. "Load the data"
2. "Calculate basic statistics"
3. "Add confidence intervals"
4. "Make it a reusable function"
5. "Add error handling"

Build incrementally!

### 6. Provide Context About Your Skill Level

```bash
claude chat "I'm new to Python. Can you explain this error in simple terms?"
```

or

```bash
claude chat "I'm comfortable with basic pandas but haven't used scipy before. Show me how to run a logistic regression."
```

### 7. Ask for Multiple Options

```bash
claude chat "What are 3 different ways I could visualize these survival curves?"
```

Claude will present options and you can pick!

---

## Common Mistakes to Avoid

### ❌ Mistake 1: Being Too Vague

**Bad:** "Fix my code"

**Better:** "My code gives error X when I try to do Y. Here's the code: [paste]"

### ❌ Mistake 2: Asking for Too Much at Once

**Bad:** "Create a complete analysis pipeline with data loading, cleaning, statistical testing, visualization, and export to Word"

**Better:** Break it into steps and ask for one piece at a time.

### ❌ Mistake 3: Not Providing Enough Context

**Bad:** "Why isn't this working?" [pastes code snippet]

**Better:** "I'm trying to calculate complication rates but getting NaN values. Here's my code: [paste]. My data looks like this: [show df.head()]"

### ❌ Mistake 4: Forgetting to Review

**Don't blindly trust AI output!**

Always:
- Read the code Claude generates
- Check if the logic makes sense clinically
- Test on a small subset first
- Verify results match your expectations

### ❌ Mistake 5: Not Asking Follow-Up Questions

If Claude's response is unclear or incomplete, **just ask again!**

```bash
claude chat "Can you explain the Wilson score interval part in simpler terms?"
```

---

## Using Claude in Your Workflow

### The Typical Vibe Coding Session

**1. Start with exploration:**
```bash
cd my_project
claude chat "I have surgical data. What should I check first?"
```

**2. Load your data:**
```bash
claude edit analysis.ipynb "Add a cell that loads data/surgical_data.csv and displays first 5 rows"
```

**3. Iterate:**
```bash
claude chat "I see some missing values in the age column. How should I handle this?"

claude edit analysis.ipynb "Add code to handle missing age values by using median imputation"
```

**4. Analyze:**
```bash
claude edit analysis.ipynb "Calculate complication rates by procedure with 95% confidence intervals"
```

**5. Visualize:**
```bash
claude edit analysis.ipynb "Create a professional bar chart of these rates"
```

**6. Export:**
```bash
claude edit analysis.ipynb "Save the figure as PNG and the results table as CSV"
```

**Total time: 30-60 minutes** for a complete analysis!

---

## Advanced Tips

### Context Is King

Claude can see files in your current directory. When working on a project:

```bash
cd my_project
claude chat "Look at my analysis.ipynb and suggest improvements"
```

Claude will read the file and give specific advice!

### Batch Requests

```bash
claude chat "
1. How do I load a CSV file?
2. How do I remove duplicates?
3. How do I calculate means by group?
"
```

Claude will answer all three!

### Ask for Alternatives

```bash
claude chat "What are the pros and cons of using a t-test vs Mann-Whitney U test for this scenario?"
```

### Request Documentation

```bash
claude edit analysis.py "Add detailed docstrings to all functions"
```

### Get Code Reviews

```bash
claude chat "Review this function and suggest improvements: [paste code]"
```

---

## Troubleshooting Your Conversations

### "Claude's response doesn't make sense"

**→ Provide more context.** Show your data structure, share error messages, explain what you're trying to accomplish.

### "Claude suggests something too complicated"

**→ Ask for simpler!** Say: "That's too advanced for me. Can you show me a simpler approach?"

### "Claude's code doesn't work"

**→ Share the error!** Copy the exact error message and ask Claude to fix it.

### "I don't understand Claude's explanation"

**→ Ask for analogy!** Say: "Can you explain this using a medical/surgical analogy?"

---

## Remember

**Claude is a tool, you're the surgeon.**

- 🧠 **You** make the clinical/scientific decisions
- 🤖 **Claude** writes the code
- 👀 **You** verify everything makes sense
- 📊 **Together** you get results fast

---

## Next Steps

Ready to see vibe coding in action with a complete example?

→ **[Next: Complete Example Analysis](example-analysis.md)**

---

## Quick Reference Card

```bash
# Ask questions
claude chat "your question"

# Create/edit files  
claude edit filename.py "what to change"

# Multi-line requests
claude chat "
Line 1
Line 2
Line 3
"

# Get help
claude --help

# See version
claude --version
```

**Golden Rule:** When in doubt, ask Claude! That's literally the point of vibe coding. 🎯
