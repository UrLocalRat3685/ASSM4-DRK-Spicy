# ASSM4-DRK-Spicy
# NBA Regular Season Analysis
NumPy · Pandas · Linear Regression · Statistical Testing

## Project Overview

This assignment analyzes NBA regular season data to uncover performance trends using Python!
The dataset was filtered to include only NBA regular season entries and statistical modeling was applied to analyze shooting performance :)

Dataset used:
players_stats_by_season_full_details.csv

## Part 1: Hidden Stories

### First I started by filtering out the data to only include the NBA regular season records!!

### A) Filtering the Dataset

The dataset was filtered to include only NBA regular season records:

```python
nba = df[(df["League"] == "NBA") & (df["Stage"] == "Regular_Season")]
```

### B) Player with the Most Regular Seasons

Then, I grouped players by name and counted the unique seasons that they played!

**Results!:**
- **Player:** Vince Carter  
- **Total NBA Regular Seasons:** 19


### C) Three-Point Accuracy by Season

Three-point accuracy was computed using:

```
3PT Accuracy = 3PM / 3PA
```

This calculation was performed for each season played by Vince Carter!

	Season	3PM	3PA	3P_pct
1	1999 - 2000	95	236	0.402542
509	2000 - 2001	162	397	0.408060
1047	2001 - 2002	121	313	0.386581
2761	2003 - 2004	93	243	0.382716
4114	2004 - 2005	127	313	0.405751
5333	2005 - 2006	125	367	0.340599
6548	2006 - 2007	156	437	0.356979
7961	2007 - 2008	98	273	0.358974
9267	2008 - 2009	151	392	0.385204
10608	2009 - 2010	119	324	0.367284
11920	2010 - 2011	116	321	0.361371
14813	2011 - 2012	74	205	0.360976
18772	2012 - 2013	162	399	0.406015
22921	2013 - 2014	146	371	0.393531
27000	2014 - 2015	69	232	0.297414
35443	2016 - 2017	112	296	0.378378
40190	2017 - 2018	57	165	0.345455
45213	2018 - 2019	123	316	0.389241
51949	2019 - 2020	61	202	0.301980


### D) Linear Regression of Three-Point Accuracy

Then I extracted the season start year (e.g., `2018` from `2018–2019`) and used it as the independent variable!!

A linear regression was performed using NumPy:

```python
m, b = np.polyfit(years, three_point_accuracy, 1)
```

**Best-fit line:**

```
y = -0.002517x + 5.42757
```

This indicates a gradual decline in three-point accuracy over time.

A scatter plot with a regression line was generated to visualize this trend, I'll leave it in the IPYNB file ^_^


### E) Average Three-Point Accuracy Using Integration

To compute the average value of the fitted line over the player’s career, the average-value formula for a linear function was used:

```
Average Value = (f(a) + f(b)) / 2
```
Which then gave us...
**Results!:**
- Average 3P% from regression line: **37.01%**
- Actual average 3P% from data: **37.00%**
- Average number of 3-pointers made per season: **114.05**

The fitted model closely matches the actual shooting performance.

---

### F) Interpolation of Missing Seasons

Vince Carter did not appear in the dataset for:
- 2002–2003
- 2015–2016

Linear interpolation was used to estimate missing three-point accuracy values

**Estimated Values:**
- 2002–2003: **38.46%**
- 2015–2016: **33.79%**

---

## Part 2 – Statistical Analysis!!

### A) Descriptive Statistics for FGM and FGA

Descriptive statistics were computed for FGM's and FGA's!

**FGM Stats!:**
- Mean: 311.48
- Variance: 25,944.08
- Skewness: 0.77
- Excess Kurtosis: 0.15

**FGA Stats!:**
- Mean: 679.86
- Variance: 118,066.75
- Skewness: 0.73
- Excess Kurtosis: 0.12

**Interpretation:**
- FGA has a much larger spread than FGM
- Both distributions are right-skewed
- Slightly heavier tails than a normal distribution

---

### B) Hypothesis Testing

#### Paired (Relational) t-Test
A paired t-test was performed comparing FGM and FGA within the same player-season rows.

**Result:**
- t-statistic: -133.01
- p-value: < 0.001

This indicates a statistically significant difference between FGM and FGA.

#### Independent Two-Sample t-Test
An unpaired t-test was also performed treating FGM and FGA as separate samples.

**Result:**
- t-statistic: -66.25
- p-value: < 0.001

**Comparison:**
- The paired t-test produced a much stronger result
- This is expected because FGM and FGA are naturally linked within each season

---

## Implementation Summary

- Pandas was used for data manipulation and filtering
- NumPy was used for numerical computation and regression
- SciPy was used for statistical testing
- Matplotlib was used for visualization
- Linear interpolation was used to estimate missing season data

---

## Limitations

- Players traded mid-season may appear multiple times per season
- Linear interpolation assumes smooth changes in performance
- Regression does not account for injuries, team changes, or role shifts
- T-tests assume approximate normality of differences

---


**AI MENTIONS LOWKEY GPT DA GOAT**
I ACCIDENTALLY BACKSPACED USING MY MOUSE AND DELETED ALMOST HALF OF THIS STUPID README. I HAD IT HELP ME OUT BY PLUGGING IN MY CODE AND MAKING IT GENERATE THE 2ND HALF IN MY STYLE OF WRITING. THIS IS SO POOP LOL
Anyways, I plugged my Jupyter file into ChatGPT, aswell as my first half of answers and asked it to generate a similar 2nd half of answers. A very good wake up call to change the keybinds on my mouse lol...
