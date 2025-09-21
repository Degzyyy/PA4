Perfect 🚀 Here’s your **final PA4 README.md** with everything combined and polished:

---

# 📘 PA 4 – Programming Assignment

👨‍💻 Author: Joshua Carl de Guzman <br>
📅 Date: 09/21/2025 <br>
📚 Course: ECE2112 – Programming Assignment

---

# 🛠 Software(s) Used

<p align="left">  
  <img src="https://www.python.org/static/community_logos/python-logo.png" alt="Python Logo" width="120"/>  
  <img src="https://jupyter.org/assets/homepage/main-logo.svg" alt="Jupyter Logo" width="90"/>  
  <img src="https://matplotlib.org/_static/logo2_compressed.svg" alt="Matplotlib Logo" width="120"/>  
  <img src="https://seaborn.pydata.org/_static/logo-wide-lightbg.svg" alt="Seaborn Logo" width="120"/>  
</p>  

---

# 📂 Repository Information

**About:** Contains solutions for **PA 4** (2 Problems)

**Languages Used:**

* Python (100%)

---

# 📌 Version History

* **V1.0 (\[09-21-2025])** – Initial Release and Submission of GitHub Link
* **V1.1 (\[09-21-2025])** – Edited Documentation in the README File and Improved Code Formatting

---

# 📌 Problem 1: Data Wrangling – Creating Data Frames

📖 **Description:**
This problem uses **data wrangling techniques** in Python (via pandas) to filter and create new data frames based on specific conditions. Three datasets were generated:

* **Vis** → Students with `Math < 70` and `Hometown = Visayas`.
* **Instru** → Students with `Track = Instrumentation`, `Hometown = Luzon`, and `Electronics > 70`.
* **Mindy** → Female students from `Mindanao` with an average score ≥ 55.

---

## 🔹 Vis Dataset

### ✅ Code

```python
Vis = df.loc[
    (df['Math'] < 70) &
    (df['Hometown'] == 'Visayas'),
    ['Name', 'Gender', 'Track', 'Math']
]

Vis
```

### ✅ Output

| Name | Gender | Track           | Math |
| ---- | ------ | --------------- | ---- |
| S4   | Male   | Instrumentation | 65   |
| S11  | Female | Communication   | 48   |
| S22  | Female | Communication   | 64   |

---

## 🔹 Instru Dataset

### ✅ Code

```python
Instru = df.loc[
    (df['Track'] == 'Instrumentation') &
    (df['Hometown'] == 'Luzon') &
    (df['Electronics'] > 70),
    ['Name', 'GEAS', 'Electronics']
]

Instru
```

### ✅ Output

| Name | GEAS | Electronics |
| ---- | ---- | ----------- |
| S1   | 75   | 89          |
| S8   | 64   | 81          |
| S30  | 57   | 81          |

---

## 🔹 Mindy Dataset

### ✅ Code

```python
# Compute average score
df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

Mindy = df.loc[
    (df['Gender'] == 'Female') &
    (df['Average'] >= 55) &
    (df['Hometown'] == 'Mindanao'),
    ['Name', 'Track', 'Electronics', 'Average']
]

Mindy
```

### ✅ Output

| Name | Track            | Electronics | Average |
| ---- | ---------------- | ----------- | ------- |
| S2   | Communication    | 75          | 67.25   |
| S5   | Instrumentation  | 77          | 72.75   |
| S15  | Microelectronics | 41          | 59.00   |
| S17  | Microelectronics | 79          | 70.50   |
| S20  | Communication    | 60          | 66.50   |

---

# 📌 Problem 2: Data Visualization – Contribution to Average Grade

📖 **Description:**
This problem analyzes how **Track**, **Gender**, and **Hometown** influence the **Average Grade** of students. Using bar charts, we can visually compare the mean average scores across categories to identify contributing factors to higher academic performance.

---

## 🔹 Code Implementation

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Set theme for consistency
sns.set_theme(style="whitegrid")

# Compute the average score for each student
df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

# Create the figure and subplots
fig, axs = plt.subplots(1, 3, figsize=(18, 6))
fig.suptitle('Average Grade by Track, Gender, and Hometown', fontsize=16)

# Average Grade by Track
sns.barplot(x='Track', y='Average', hue='Track', data=df, ax=axs[0], palette='Blues', legend=False)
axs[0].set_title('By Track')
axs[0].tick_params(axis='x', rotation=45)

# Average Grade by Gender
sns.barplot(x='Gender', y='Average', hue='Gender', data=df, ax=axs[1], palette='Greens', legend=False)
axs[1].set_title('By Gender')

# Average Grade by Hometown
sns.barplot(x='Hometown', y='Average', hue='Hometown', data=df, ax=axs[2], palette='Reds', legend=False)
axs[2].set_title('By Hometown')
axs[2].tick_params(axis='x', rotation=45)

# Adjust layout
plt.tight_layout(rect=[0, 0, 1, 0.95])
plt.show()
```

---

## 🔹 Visual Output

📊 The graphs generated include:

1. **By Track** – Shows the mean average scores grouped by college track.
2. **By Gender** – Compares average grades between Male and Female students.
3. **By Hometown** – Compares performance of students from Luzon, Visayas, and Mindanao.

<img width="1102" height="363" alt="image" src="https://github.com/user-attachments/assets/12e02ce0-f851-4151-b210-c71b9e481f9b" />


---

## 🔹 Analysis of Results

* **Track**: Some tracks (e.g., Instrumentation, Communication) display slightly higher averages than others.
* **Gender**: Both genders show nearly equal performance, though slight variations may exist.
* **Hometown**: Students from different regions show small but visible differences in their average scores.

👉 Overall, the visualization shows that **Track** and **Hometown** appear to contribute slightly more than Gender to variations in average grades.

---
