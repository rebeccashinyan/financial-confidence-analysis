# Mind over Money: Financial Confidence, Competence, and Well-Being

A data analysis project examining the mismatch between **financial confidence** and **financial competence**, and how that mismatch relates to indicators of financial well-being and financial behavior.

This project uses the **2024 National Financial Capability Study (NFCS) State-by-State Survey** and builds a simple quadrant framework to compare people who are:
- low confidence / low competence
- low confidence / high competence
- high confidence / low competence
- high confidence / high competence

The project also includes predictive modeling to test whether selected financial behavior variables can predict a person’s confidence or competence level. The project title, team framing, and dataset context are reflected in the presentation. {index=12}

---

## Project Questions

This project focuses on three main questions:

1. How does financial confidence relate to financial competence?
2. How do overconfident and underconfident people differ in financial well-being outcomes?
3. Can selected financial behavior variables predict financial confidence or competence?

---

## Dataset

**Source:** 2024 National Financial Capability Study (NFCS) State-by-State Survey  
**Population:** U.S. adults age 18+ across all 50 states  
**Approximate size:** ~25,539 respondents :contentReference[oaicite:13]{index=13}

The notebook uses:
- `M4` for self-reported financial confidence
- `M6`–`M10` (“Big Five”) for financial literacy / competence
- selected `J` and other survey variables for behavioral and financial well-being comparisons

---

## Key Variables

### Financial Confidence
Confidence is derived from `M4`:
- **Low confidence** = responses 1–5
- **High confidence** = responses 6–7

### Financial Competence
Competence is derived from the Big Five literacy questions:
- `M6`, `M7`, `M8`, `M9`, `M10`

A respondent’s **Competence Score** is the number of correct answers (0–5):
- **Low competence** = 0–3 correct
- **High competence** = 4–5 correct

---

## Quadrant Framework

Each respondent is placed into one of four groups:

- **Realistic-Low** = low confidence, low competence
- **Underconfident** = low confidence, high competence
- **Overconfident** = high confidence, low competence
- **Realistic-High** = high confidence, high competence

This quadrant framework is the core structure used throughout the visual analysis.

---

## Data Cleaning and Processing

The notebook performs the following steps:

- loads the NFCS 2024 state-level survey data
- checks for null values and duplicates
- removes invalid self-confidence responses in `M4` (`98`, `99`)
- treats invalid responses in the Big Five literacy questions as incorrect
- creates binary confidence and competence variables
- recodes selected financial behavior variables for visualization
- fills missing values with median values for the predictive modeling feature matrices

---

## Analysis Workflow

### 1. Exploratory / Descriptive Analysis
The notebook first examines the distributions of:
- self-reported financial confidence
- actual financial literacy score
- confidence vs. competence cross-tabulation

### 2. Quadrant-Based Outcome Analysis
The notebook then compares the four groups across selected outcomes, including:
- debt collection contact
- spending vs. income
- difficulty paying bills
- emergency $2,000 confidence
- self-rated credit
- financial satisfaction
- homeownership

### 3. Composite Comparison
The notebook creates a normalized comparison across outcome variables to summarize relative quadrant performance.

### 4. Predictive Modeling
Two Random Forest classifiers are trained:
- one to predict **Confidence**
- one to predict **Competence**

---

## Notebook Results

### Distribution of Confidence
- **Low confidence:** 16,347 respondents (65.3%)
- **High confidence:** 8,683 respondents (34.7%)

### Distribution of Competence
- **Low competence:** 16,115 respondents (64.4%)
- **High competence:** 8,915 respondents (35.6%)

### Confidence vs. Competence Cross-Tab
- **Realistic-Low:** 11,649
- **Underconfident:** 4,698
- **Overconfident:** 4,466
- **Realistic-High:** 4,217

A notable pattern is that **underconfidence is slightly more common than overconfidence** in this sample.

---

## Predictive Modeling Results

### Confidence Model
A Random Forest classifier is trained using:
- `J3`
- `J4`
- `J20`
- `J32`
- `J63`

**Accuracy:** 0.64

Top feature importances:
1. `J20`
2. `J32`
3. `J63`
4. `J4`
5. `J3`

### Competence Model
A Random Forest classifier is trained using:
- `J3`
- `J4`
- `J20`
- `J5`
- `J8`

**Accuracy:** 0.67

Top feature importances:
1. `J20`
2. `J5`
3. `J8`
4. `J4`
5. `J3`

Overall, the notebook’s results suggest that **competence is somewhat easier to predict than confidence**, likely because competence is tied more directly to observable financial behaviors.

---

## Main Takeaways

- Financial confidence and financial competence are related, but they are not the same thing.
- Mismatches between confidence and competence are common.
- Underconfident and overconfident groups show different financial outcome patterns.
- Competence appears slightly more predictable than confidence in the notebook’s modeling setup.
- Self-perception and actual knowledge should be studied separately when analyzing financial decision-making.

---

## Files

- `financial_confidence_analysis.ipynb` — main notebook
- presentation slides — project presentation / storytelling deck :contentReference[oaicite:14]{index=14}

---

## Tools Used

- Python
- pandas
- NumPy
- matplotlib
- seaborn
- scikit-learn

---

## Limitations

- The project uses threshold-based binarization for both confidence and competence.
- Several outcome interpretations are descriptive rather than causal.
- Random Forest performance is moderate, not high, so results should be interpreted carefully.
- Some presentation statements may not exactly match the final notebook outputs.

---

## Authors

Presentation credits list:
- Makaila Kim
- Alex Reifel
- Rebecca Wang :contentReference[oaicite:15]{index=15}
