# 📊 Job Market Analysis – Power BI Dashboard

This repository contains a complete Power BI project that analyzes the **Data Science & Analytics job market** using real-world job postings data.  
The report explores job demand, salaries, locations, company ratings, and skills required for different job titles.

### 📊 Job Market Overview
<img width="1309" height="735" alt="image" src="https://github.com/user-attachments/assets/2a84efbb-4531-4000-841b-ab2daaa495ca" />

---

## 🚀 Project Overview

The **Job Market Analysis** dashboard helps answer questions such as:

- How many jobs are available across companies, industries, and states?
- What are the **top job titles** and their **salary ranges**?
- Which **states and companies** have the most job openings?
- What is the **average salary by state, job title, and education level**?
- Which **technical skills** (Python, SQL, AWS, etc.) are most in demand for each role?

The project is built end-to-end in **Power BI**, from data cleaning and modeling to DAX measures and interactive visuals.

---

## 📁 Dataset Description

This repo includes four main CSV files (rename the paths if your structure is different):

1. **`Job Market Analysis RAW DATA.csv`**  
   - Original raw job postings data.
   - Typical fields: job title, company, location, salary range, rating, job description, etc.
   - Used as the starting point for cleaning and transformation.

2. **`Job Market Analysis.csv`**  
   - Cleaned and transformed **fact table** used in the Power BI model.  
   - Example columns:
     - `Job_ID`
     - `Job_Title`
     - `Job_Category`
     - `Company_Name`
     - `State`
     - `Industry`
     - `Min_Salary`, `Max_Salary`, `Avg_Salary`
     - `Company_Rating`
     - `Education_Level`
     - `Job_Posted_Date`, etc.

3. **`Reference_DIM_Job_Table.csv`**  
   - Dimension table containing standardized job information.  
   - Example columns:
     - `Job_Title`
     - `Job_Category` (Data Analyst, Data Engineer, Data Scientist, ML Engineer, etc.)
     - Mapping used to group similar titles and build cleaner visuals.

4. **`Reference_JobTitle_Category_Skills.csv`**  
   - Skills mapping table used to build the **skills heatmap**.
   - Example columns:
     - `Job_Category`
     - Skill flags/counts (e.g., `Python`, `SQL`, `Excel`, `Tableau`, `AWS`, `Spark`, `TensorFlow`, etc.)
   - Shows how many companies require each skill for each job category.

> 🔁 You can easily extend these reference tables to add new job titles or skills.

---

## 🧱 Data Model (Power BI)

The model follows a **star schema**:

- **Fact Table**
  - `Job Market Analysis` – main job postings table.

- **Dimension Tables**
  - `DIM_Job` (from `Reference_DIM_Job_Table.csv`)
  - `DIM_Skills` / job category skills (from `Reference_JobTitle_Category_Skills.csv`)
  - Optional: `DIM_State`, `DIM_Company`, `DIM_Date` (if you create them).

Key relationships (examples):

- `Job Market Analysis[Job_Title]` → `DIM_Job[Job_Title]`
- `DIM_Job[Job_Category]` → `Reference_JobTitle_Category_Skills[Job_Category]`
- `Job Market Analysis[State]` → `DIM_State[State]`

---

## 📈 Dashboard Pages & Visuals

### 🔹 Page 1 – Job Market Overview

Main KPIs:

- **Total Jobs**
- **Total Companies**
- **Total Industries**
- **Overall Average Salary**
- **Average Company Rating**

Key visuals:

- **Donut Chart** – Top 5 industries by number of job postings.
- **Bar Chart** – Average minimum & maximum salary by state.
- **Bar/Line Combo** – Salary vs job count for top job titles.
- **Bar Chart** – States with the most number of jobs.
- **Treemap** – Companies with the most job openings.
- **Slicers** – Job Title, State (applied to all visuals).

---

### 🔹 Page 2 – Roles, Education & Skills

Key visuals:

- **Job Title Buttons** (Data Analyst, Data Engineer, Data Scientist, ML Engineer, Director, etc.) for quick filtering.
- **Pie Chart** – Average salary vs education level (Bachelor/Master/PhD/Not Applicable).
- **Column Chart** – Top job titles by job count.
- **Filled Map** – Average salary by state (US map).
- **Skills Heatmap** –  
  *“Skills Required by Companies for Each Job Title”*  
  Shows the number of postings that require skills like:
  - Python, R, SQL, Excel, Tableau
  - AWS, Spark, Hadoop, BI tools
  - TensorFlow, PyTorch, Keras, etc.

---

## 🛠 Tech Stack

- **Power BI Desktop**
- **Power Query** – Data cleaning & transformation.
- **DAX** – Calculated columns, measures, KPIs (e.g., job count, avg salary, average rating).
- **CSV Files** – As data source.

---

## 📂 Suggested Folder Structure

```text
.
├── data/
│   ├── Job Market Analysis RAW DATA.csv
│   ├── Job Market Analysis.csv
│   ├── Reference_DIM_Job_Table.csv
│   └── Reference_JobTitle_Category_Skills.csv
├── reports/
│   └── Job Market Analysis.pbix
├── images/
│   ├── Job-Market-Overview.png
│   └── Job-Market-Skills.png
└── README.md
