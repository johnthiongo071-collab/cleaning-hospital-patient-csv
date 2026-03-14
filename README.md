# 🏥 Hospital Patients — Advanced Data Analysis

**Notebook:** `patients_advanced_analysis.ipynb`  
**Dataset:** `hospital_patients_real_world.csv`  
**Libraries:** pandas, matplotlib, seaborn, scipy, numpy

This notebook is an extended visual analysis of hospital patient records. It builds on the cleaned dataset from `patients_enhanced.ipynb` and introduces a wider range of chart types to explore patient demographics, diagnoses, temporal admission patterns, correlations, and extended stay profiling.

---

## 🚀 How to Run

1. Place `hospital_patients_real_world.csv` in the same directory as the notebook
2. Install dependencies:
   ```bash
   pip install pandas matplotlib seaborn scipy numpy
   ```
3. Open and run all cells top to bottom:
   ```bash
   jupyter notebook patients_advanced_analysis.ipynb
   ```

> **Note:** Section 4 (Billing Amount Analysis) requires a `BillingAmount` column in the dataset. If your dataset does not include it, skip that section — all other sections will run without it.

---

## 📁 Notebook Structure

| Section | Title |
|---------|-------|
| 1 | Setup & Data Preparation |
| 2 | Patient Demographics |
| 3 | Diagnosis Deep Dive |
| 4 | Temporal Patterns |
| 5 | Correlation Matrix |
| 6 | Extended Stay Profiling |
| 7 | Pair Plot |
| 8 | Final Summary Dashboard |
| 9 | Key Findings |

---

## 📊 Visuals Explained

### Section 2 — Patient Demographics

**2.1 Age Group Donut Chart**  
A donut chart showing what percentage of all patients falls into each of five age groups: Child, Teenager, Young Adult, Middle-Aged, and Senior. The total patient count is printed at the centre. This gives an instant overview of who the typical patient is.

**2.2 Age Distribution — Violin + Strip Plot**  
A violin plot overlaid with a random sample of individual data points (strip plot) for each age group. The width of the violin at any point shows how many patients fall at that age. The scattered white dots on top reveal the actual density of individual records, making it easy to spot where ages cluster within each group.

---

### Section 3 — Diagnosis Deep Dive

**3.1 Stacked Bar — Diagnosis Share by Age Group**  
A horizontal stacked bar chart for the top 10 diagnoses. Each bar adds up to 100% and is divided into coloured segments representing the proportion of patients from each age group. This lets you compare, for example, whether a diagnosis like pneumonia skews heavily towards seniors while another condition is more evenly spread across age groups.

**3.2 Box Plot — Length of Stay per Diagnosis**  
A horizontal box plot showing the spread of length of stay (in days) for each of the top 10 diagnoses, sorted from longest to shortest median stay. Each box captures the interquartile range (middle 50% of stays), the line inside marks the median, and the dots beyond the whiskers are outliers. This makes it straightforward to see which diagnoses consistently result in long stays and which show high variability.

---

### Section 4 — Temporal Patterns

**4.1 Admissions by Day of the Week**  
A bar chart counting how many patients were admitted on each day of the week, Monday through Sunday. Weekday bars are shown in blue and weekend bars in coral, making it easy to spot whether the hospital sees fewer admissions on Saturdays and Sundays — a pattern common in non-emergency settings.

**4.2 Monthly Admissions Heatmap (Year × Month)**  
A heatmap where each row is a year and each column is a month. The colour intensity and annotated number in each cell show how many admissions occurred in that particular month and year. Darker cells indicate busier periods. This is useful for identifying recurring seasonal peaks or spotting unusual spikes in a specific period.

**4.3 Seasonal Admissions — Grouped Bar by Age Group**  
A grouped bar chart with one cluster of bars for each season (Spring, Summer, Autumn, Winter). Within each cluster, a separate bar represents one age group. This lets you compare both how overall admissions vary by season and whether certain age groups drive those seasonal shifts more than others.

---

### Section 5 — Correlation Matrix

**Correlation Heatmap**  
A lower-triangle heatmap showing the Pearson correlation coefficient between every pair of numeric columns in the dataset. Values range from –1 (perfect negative correlation) to +1 (perfect positive correlation), with 0 meaning no linear relationship. The colour scale goes from red (negative) through yellow (neutral) to green (positive). Showing only the lower triangle avoids redundancy since the matrix is symmetrical.

---

### Section 6 — Extended Stay Profiling

Extended stay is defined as any admission where `LengthOfStay` exceeds the 75th percentile of the dataset. The threshold value is printed when this section runs.

**6.1 Extended Stay Rate by Age Group**  
A bar chart showing what percentage of patients in each age group had an extended stay. The bar with the highest rate is highlighted in coral; all others are blue. A dashed horizontal line marks the overall extended stay rate across all patients, making it easy to see which age groups are above or below average.

**6.2 Extended Stay Rate by Diagnosis (Top 10)**  
A horizontal bar chart ranking the top 10 diagnoses by their extended stay rate, sorted from lowest to highest. Bars are coloured on a red-yellow-green gradient, with red indicating diagnoses where extended stays are most common. This helps identify which conditions are most associated with prolonged hospitalisation.

**6.3 Split Violin — Extended vs Normal Stay by Age Group**  
A split violin plot where each age group has two halves: the left half (blue) shows the length of stay distribution for normal-stay patients and the right half (coral) shows it for extended-stay patients. Quartile lines are drawn inside each violin. This makes it possible to compare not just the average but the full shape of the stay distribution between the two groups, within each age band.

---

### Section 7 — Pair Plot

**Multi-Variable Pair Plot**  
A corner pair plot comparing every combination of available numeric variables (Age, LengthOfStay, and BillingAmount if present). Each off-diagonal panel is a scatter plot of two variables, and the diagonal panels show a KDE (kernel density estimate) of each variable's distribution. All points are coloured by age group. This is a broad-sweep view useful for spotting correlations and distribution differences that are worth investigating further.

---

### Section 8 — Final Summary Dashboard

A single 3×3 multi-panel figure saved as `dashboard.png` that brings together six key charts in one place:

| Panel | Chart |
|-------|-------|
| Top-left | Donut — age group share |
| Top-centre | Horizontal bar — top 5 diagnoses |
| Top-right | Bar — extended stay rate by age group with overall average line |
| Middle (full width) | Line chart — monthly admissions over time with shaded fill |
| Bottom-left & centre | Violin — length of stay by age group |
| Bottom-right | Bar — admissions by day of the week (weekends highlighted) |

This dashboard is designed to be a self-contained summary that can be exported and shared without opening the full notebook.

---

## 🛠️ Skills Demonstrated

- Data wrangling and feature engineering with **pandas**
- A wide range of visualisation types using **matplotlib** and **seaborn**
- Donut, violin, strip, box, stacked bar, bubble, grouped bar, heatmap, pair plot, and dashboard layouts
- Temporal decomposition (day-of-week, month, season, year)
- Correlation analysis using Pearson r
- Statistical profiling with IQR-based segmentation
- Multi-panel figure composition with `GridSpec`
