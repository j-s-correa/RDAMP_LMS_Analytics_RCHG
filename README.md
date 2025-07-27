# 📊 RCHG LMS Analytics Project

## ✅ Project Overview
This project focuses on cleaning and preparing an LMS dataset enriched with employee information, and building **Power BI and Tableau dashboards** to analyse compliance, training performance, and engagement patterns.

---

## 🧹 1. Data Cleaning and Preparation Report

### **Project Objective**
Prepare a clean, standardised LMS dataset enriched with employee details, ready for Power BI dashboards and analytics.

---

### **Steps Taken**

#### **1. Data Integration**
- Combined the **LMS dataset** with **Employee Info** using `EmployeeID` as the key.
- Added `JoinedDate` from Employee Info and placed it next to `EnrollmentDate` for logical flow.

#### **2. Data Cleaning**
- **Verified Binary Columns**:
  - Columns like `IsMandatory` and `Overdue` checked for valid values (**Yes/No**).
  - Corrected **15 misclassified entries** to `No`.
- **Standardized Column Names**:
  - Removed spaces and replaced them with underscores for compatibility.
  - Example: `Course Title → Course_Title`.
- **Removed Duplicates**:
  - Eliminated duplicate rows to maintain data integrity.

#### **3. Date Standardisation**
- Converted all relevant columns to `datetime` format:
  - `EnrollmentDate`, `CompletionDate`, `LastAccessDate`, `JoinedDate`.
- Applied consistent **DD-MM-YYYY** format.

#### **4. Derived Metrics and Flags**
- Added **calculated columns**:
  - `DaysSpent = CompletionDate − EnrollmentDate`
  - `Enroll_minus_Join = EnrollmentDate − JoinedDate`  
    → Positive = OK, Negative = Anomaly.
  - `Days_LastAccess_vs_Completion = LastAccessDate − CompletionDate`.
- **Flags Added**:
  - `CourseBeforeEmployee` = TRUE if enrollment occurred before joining.

#### **5. Validation and Export**
- Verified cleaned data for anomalies.
- Exported final datasets for Power BI:
  - `Final_Enriched_LMS_Dataset.xlsx`
  - `Cleaned_RCHG_LMS_Dataset_For_PowerBI.xlsx`

#### **6. Notebook Automation**
- Developed a **Google Colab script**:
  - Mount Google Drive & import libraries (pandas, numpy, openpyxl).
  - Load dataset → Remove duplicates → Standardize names.
  - Export cleaned dataset for Power BI.

---

### ✅ **Summary of Key Changes**
✔ Binary fields standardized (**Yes/No**)  
✔ 15 incorrect entries corrected  
✔ Added metrics for course duration and anomalies  
✔ Flags for employees enrolled before joining  
✔ Exported Power BI-ready Excel files  

---

## 📈 2. Dashboard Components
The dashboards are designed to provide insights into **Compliance & Training Summary**, **Performance Analysis**, and **Engagement Patterns**.

---

### **A. Compliance & Training Summary**
- **% of Completed Mandatory Courses**  
  → Breakdown by **team and role** with color-coded bars.  
  → Added **employee counts** for better context.

- **Overdue Training Trends**  
  → Monthly trends + Year-over-Year (YoY) view.  
  → Helps identify **seasonal peaks** in overdue training.

---

### **B. Performance Analysis**
- **SkillScore Distribution**  
  → Average ratings for **Communication**, **Teamwork**, and **Technical Efficiency** by **team** and **role**.  
  → Shows consistency in training quality and gaps across roles.

- **Flagged Skill Gaps**  
  → Stacked bars showing **Yes/No percentages**.  
  → Helps HR target **critical roles** with the highest skill gaps.

- **Average Review Score by Role and Team**  
  → Horizontal bar charts showing **mean scores**.  

---

### **C. Engagement Patterns**
- **Access Trends (Enrollment vs Last Access)**  
  → Dual-line chart comparing **enrollment vs last access activity** over time.  
  → Indicates drop-off rates and user engagement.

- **Device Usage Breakdown**  
  → Pie chart of access via **Desktop**, **Mobile**, and **Tablet**.

- **Time Spent on Courses**  
  → Average **course duration in minutes** by:
    - **Role**
    - **Location**

---

## 🛠️ Tools Used
- **Tableau Public** → Visualisation for trends and breakdowns.
- **Python (Pandas, NumPy)** → Data cleaning and automation.
- **Google Colab** → Notebook-based pipeline for data prep.

  <img width="532" height="511" alt="image" src="https://github.com/user-attachments/assets/6d3a6366-11d8-4800-9de6-2cc4a688b85a" />


---

## 📂 Files in Repository
- `Final_Enriched_LMS_Dataset.xlsx` – Cleaned dataset for Power BI.
[Final_Enriched_LMS_Dataset.xlsx](https://github.com/user-attachments/files/21448364/Final_Enriched_LMS_Dataset.xlsx)


---

## ✅ How to Use
1. Download the **cleaned dataset** from this repo.
2. Open the **Power BI report** or **Tableau workbook**.
3. Connect data → Explore dashboards.

---


## 📊 2. LMS Dashboard Analysis

### 📊 Explore the Interactive Dashboards
All visualisations were built using **Tableau Public**.  
👉 [**Click here to view the full dashboards**](https://public.tableau.com/app/profile/juan.correa./viz/LMS-RychtenshaneCommunityHousingGroupRCHG/EngagementLearningBehaviourAnalysis)

---

## ✅ Overview
This project analyses **Learning Management System (LMS)** data to monitor training compliance, engagement patterns, and employee performance across teams and roles.

Dashboards were built using **Tableau Public** with data on enrollments, last access dates, skill scores, and device usage.

---

## 📌 Key Dashboards & Insights

### 1. Compliance & Training Summary
- **% of Completed Mandatory Courses by Team**
  - IT: **82.79%**
  - Facilities: **81.52%**
  - Repairs: **79.55%**
- **Overdue Training Trends**
  - Peak overdue: **62 employees in 2022**
  - Monthly highest overdue: **June with 9 overdue courses**
    
<img width="890" height="728" alt="image" src="https://github.com/user-attachments/assets/2ba8796b-2665-40a9-905d-e7b719cf4f1e" />
<img width="881" height="735" alt="image" src="https://github.com/user-attachments/assets/a1bb997b-10b8-464a-b8ff-53852cb26d91" />

> **Note:** Even after creating new aggregated columns in Python and Excel during earlier steps, we decided to compute the **Completed and Mandatory** ratio directly in Tableau. This approach was chosen for the quicker calculation of the indicator by leveraging Tableau’s native aggregation, rather than relying on pre-processed data.

<img width="1385" height="841" alt="image" src="https://github.com/user-attachments/assets/c224116b-29be-46c4-bc5d-9dcf3a04e124" />
  
### 2. Performance Analysis
- **SkillScore Distribution** (Scale: 1–5)
  - Communication: Facilities highest (**3.11**), Housing lowest (**2.92**)
  - Teamwork: IT highest (**3.05**)
  - Tech Efficiency: Finance highest (**3.16**)
- **Skill Gaps**
  - IT team has the highest flagged gaps (**17.55%**)
- **Average Review Scores**
  - Highest: Electrician (**81.83**)
  - Lowest: Plumber (**78.82**)
    
<img width="908" height="723" alt="image" src="https://github.com/user-attachments/assets/f632274d-0194-4e5b-97b5-ba42998176ff" />
<img width="902" height="730" alt="image" src="https://github.com/user-attachments/assets/8d7ebc00-f59a-4cda-82ef-16eb9328edf4" />
<img width="921" height="728" alt="image" src="https://github.com/user-attachments/assets/c20354af-6ebf-4f67-be93-1904024f14ba" />


### 3. Engagement Patterns
- **Access Trends (Enrollment vs Last Access)**
  - Enrollment peak: **189 in 2024**
  - Last Access peak: **179 in 2024**
- **Device Usage Breakdown**
  - Desktop: **56.11%**
  - Mobile: **51.93%**
  - Tablet: **51.83%**
- **Time Spent on Courses**
  - By Role:
    - Lettings Coordinator: **78 mins**
    - Plumber: **70.2 mins**
  - By Location:
    - Northfield Office: **76.4 mins**

<img width="920" height="725" alt="image" src="https://github.com/user-attachments/assets/18bd5ab7-f228-4256-9ae2-e6a28de5390b" />
<img width="915" height="723" alt="image" src="https://github.com/user-attachments/assets/e4d6f6bb-b13b-4477-83eb-bcb350657020" />

---

## 🛠 Tech Stack
- **Visualization Tool:** Tableau Public
- **Dataset:** LMS Employee Training Data
- **Data Cleaning & Prep:** Excel/Python

---

### 🔍 Next Steps
- Add **predictive modeling** for training completion trends.
