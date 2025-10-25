# 🏥 ER Patient Flow & Doctor Performance Dashboard

## 📘 Project Overview

This project, **ER Patient Flow & Doctor Performance Dashboard**, is an end-to-end Power BI analytics solution designed to analyze **Emergency Room (ER) performance** and **Doctor efficiency** within a healthcare environment.

The dashboard integrates patient and doctor datasets to provide a unified, interactive visualization platform. It helps administrators and decision-makers monitor **patient wait times**, **departmental efficiency**, **doctor revenue performance**, and **overall ER operations** in real time.

---

## 🎯 Project Objectives

* Analyze **ER patient visits** and traffic by department.
* Track and improve **average patient wait times**.
* Measure **doctor revenue** and **patients served**.
* Evaluate **wait time success percentage** as a key performance metric.
* Deliver an **interactive Power BI dashboard** with slicers, KPIs, and visuals.

---

## 🗂️ Files Used in This Project

| File Name                                 | Description                                                                   |
| ----------------------------------------- | ----------------------------------------------------------------------------- |
| `Hospital ER.csv`                         | Contains ER patient data including department, wait times, and gender.        |
| `Doctor_Patients_data.xlsx`               | Contains doctor data with patient IDs, department referrals, and doctor fees. |
| `ER_Doctor_Performance_Dashboard.pbix` | Main Power BI dashboard file combining both datasets.                         |
| `ER_Doctor_Performance_Dashboard-2.pdf`   | Exported PDF version of the Power BI dashboard for portfolio viewing.         |

All these files are available in the repository: **PowerBI_ER_Doctor_Performance_Analysis**.

---

## 🧩 Data Model: Star Schema Design

The dashboard follows a **Star Schema Model** for performance optimization and clarity.

### **Tables:**

1. **ER_Data (Fact Table)** – Patient ER visit details and wait times.
2. **Doctor_Data (Fact Table)** – Doctor performance and patient-level data.
3. **Dim_Department (Dimension Table)** – Contains unique department names for model linkage.

### **Relationships:**

* `Dim_Department[department_referral]` → `ER_Data[department_referral]` (1:Many)
* `Dim_Department[department_referral]` → `Doctor_Data[department_referral]` (1:Many)

---

## ⚙️ Data Cleaning and ETL Process

All data transformations were performed in **Power Query Editor** in Power BI.

### **Steps Followed:**

1. **Import Datasets:** Loaded both `Hospital ER.csv` and `Doctor_Patients_data.xlsx` into Power BI.
2. **Column Formatting:** Defined appropriate data types for numerical, text, and datetime fields.
3. **Standardized Department Names:**

   * Issue: Inconsistent naming caused slicers to show blanks.
   * Fix: Applied transformations — `Clean`, `Trim`, and `Capitalize Each Word`.
4. **Created Dimension Table:**

   ```DAX
   Dim_Department = DISTINCT('Doctor_Data'[department_referral])
   ```
5. **Established Relationships:** Linked both fact tables with `Dim_Department`.

---

## 🧮 DAX Measures and KPIs

### **ER_Data Table**

| Measure                                                                                           | Formula                                                       | Description                           |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------- |
| **Total ER Visits**                                                                               | `Total ER Visits = COUNT('ER_Data'[patient_id])`              | Total patient visits to the ER.       |
| **Avg Wait Time (Mins)**                                                                          | `Avg Wait Time (Mins) = AVERAGE('ER_Data'[Wait Time (Mins)])` | Average waiting time for ER patients. |
| **Wait Time Success %**                                                                           | ```DAX                                                        |                                       |
| Wait Time Success % =                                                                             |                                                               |                                       |
| VAR TotalVisits = COUNT('ER_Data'[patient_id])                                                    |                                                               |                                       |
| VAR SuccessfulVisits = CALCULATE(COUNT('ER_Data'[patient_id]), 'ER_Data'[Wait Time (Mins)] <= 30) |                                                               |                                       |
| RETURN DIVIDE(SuccessfulVisits, TotalVisits)                                                      |                                                               |                                       |

```| Percentage of ER cases where waiting time ≤ 30 minutes. |

### **Doctor_Data Table**
| Measure | Formula | Description |
|----------|----------|-------------|
| **Total Doctor Revenue** | `Total Doctor Revenue = SUM('Doctor_Data'[Doctor Fee])` | Total revenue generated by all doctors. |
| **Total Patients Served** | `Total Patients Served = DISTINCTCOUNT('Doctor_Data'[patient_id])` | Number of unique patients served per doctor. |

---

## 📊 Dashboard Design & Visuals
### **Dashboard Title:**  
> *ER Patient & Doctor Performance Dashboard*

### **Visual Elements:**
| Component | Type | Description |
|------------|------|-------------|
| **Card 1** | KPI Card | Displays `Total ER Visits`. |
| **Card 2** | KPI Card | Displays `Avg Wait Time (Mins)`. |
| **Card 3** | KPI Card | Displays `Wait Time Success %`. |
| **Card 4** | KPI Card | Displays `Total Doctor Revenue`. |
| **Slicer 1** | Dropdown | Department selector (`department_referral`). |
| **Slicer 2** | Dropdown | Doctor Name filter. |
| **Chart 1** | Clustered Column Chart | `Total ER Visits` by `department_referral`. |
| **Chart 2** | Donut Chart | `Total ER Visits` by `patient_gender`. |
| **Table Visual** | Table | Displays `Doctor Name`, `Total Doctor Revenue`, `Total Patients Served`, and `Avg Wait Time (Mins)`. |

---

## 🧠 Troubleshooting & Fixes
| Issue | Root Cause | Resolution |
|-------|-------------|-------------|
| Red underline in DAX formula | Hidden spaces or mismatched column names | Copied exact column name from Data View. |
| Slicer filtering only Orthopaedics | Hidden characters in department names | Used Power Query **Clean**, **Trim**, and **Capitalize**. |
| GitHub upload error for PBIX | File exceeded upload limit | Used **GitHub Desktop** to commit and push the file. |

---

## 💾 Deployment Instructions
1. **Create a GitHub Repository:** `PowerBI_ER_Doctor_Performance_Analysis`  
2. **Upload Files:**  
   - `AR_ER_Doctor_Performance_Dashboard.pbix`  
   - `Hospital ER.csv`  
   - `Doctor_Patients_data.xlsx`  
   - `ER_Doctor_Performance_Dashboard-2.pdf`  
   - `README.md` (this file)
3. **For Large PBIX Files (>25MB):**  
   - Use **GitHub Desktop** → Clone Repo → Copy `.pbix` → Commit & Push.

---

## 🏗️ Tools & Technologies
- **Power BI Desktop**  
- **Power Query Editor**  
- **DAX (Data Analysis Expressions)**  
- **Excel / CSV Data Sources**  

---

## 📈 Key Insights
- Orthopaedics department had the **highest ER visits**.  
- The **average wait time** was reduced significantly after cleaning inconsistent data.  
- **Doctor revenue** strongly correlated with patient throughput.  
- The **Wait Time Success %** metric effectively identified top-performing departments.

---

## 🧾 Summary
This Power BI project demonstrates end-to-end **data modeling**, **ETL**, **DAX measure creation**, and **dashboard development** following industry best practices. It showcases:
- Mastery of Power BI reporting and interactivity.  
- Strong analytical and visualization skills.  
- Proficiency in data relationships, KPIs, and performance metrics.  

---

## 👨‍💻 Author
**AR**  
Power BI Developer | Data Analyst  
📍 Project: *ER Patient Flow & Doctor Performance Dashboard*  
💼 Repository: [PowerBI_ER_Doctor_Performance_Analysis](#)

```
