# 📊 Healthcare Business Analyst Case Study  

[![SQL](https://img.shields.io/badge/Skills-SQL-blue)](Healthcare_BA_Case_Study.sql)
[![Power BI](https://img.shields.io/badge/Skills-PowerBI-yellow)]()
[![Business Analysis](https://img.shields.io/badge/Focus-Process%20Improvement-green)]()
[![Domain](https://img.shields.io/badge/Domain-Healthcare-red)]()

---

## 🩺 Project Overview  
This case study demonstrates how a **Business Analyst** applied requirements gathering, process mapping, and data analytics to improve **utilization management (UM)**, **clinical quality reporting (HEDIS/STAR)**, and **nurse workflow efficiency** for a mid-sized health insurer.  

The project highlights measurable impact in **efficiency, compliance, and patient outcomes** through **business analysis and SQL-driven insights**.

---

## ⚠️ Business Problem  
The organization struggled with:  
- ⏳ Long **prior authorization turnaround times**  
- 📉 Inconsistent **clinical quality reporting** (HEDIS/STAR)  
- 🧑‍⚕️ Manual workloads overwhelming nurse case managers  
- 🔍 Limited **population health visibility**  

---

## 🎯 Objectives  
- Reduce prior authorization turnaround time by **20%**  
- Automate and standardize **HEDIS/STAR reporting**  
- Save nurse case managers **6+ hours per week**  
- Improve dashboards for **high-risk patient monitoring**  

---

## 🔧 Approach  
- **Requirements Gathering** → Stakeholder interviews, As-Is / To-Be workflows (Lucidchart)  
- **SQL + Data Analysis** → Extracted, cleaned, and aggregated claims & clinical data  
- **Power BI Mock Dashboards** → Visualized turnaround time, compliance trends, nurse productivity  
- **System Configuration** → Auto-approval rules for low-risk requests  
- **Change Management** → UAT + staff training  

---

## 🚀 Results  
| Metric                          | Before | After | Impact        |
|--------------------------------|--------|-------|---------------|
| Prior Auth Turnaround (days)   | 10     | 7.3   | **27% faster** |
| HEDIS Compliance Errors        | High   | Low   | **-40%**      |
| Nurse Manual Hours Saved       | 0      | 6/wk  | **+6 hrs**    |
| ER Admissions (high-risk)      | Higher | Lower | Improved      |

✅ Stronger compliance with **NCQA / CMS**  
✅ Nurses shifted focus from admin work to **patient care**  

---

## 📂 Deliverables  
- 📄 [Case Study PDF](Healthcare_BA_Case_Study_Visuals.pdf)  
- 🧑‍💻 [SQL Script](Healthcare_BA_Case_Study.sql)  
- 📈 Dashboard-Style Visuals:  
  - ![Turnaround Time](Turnaround_Time.png)  
  - ![HEDIS Compliance](HEDIS_Compliance.png)  
  - ![Nurse Time Savings](Nurse_Time.png)  

---

## 🧑‍💻 SQL Script (Excerpt)  

```sql
-- Prior Authorization Turnaround (Before vs After)
SELECT
  CASE WHEN request_dt::date < DATE '2025-01-15'
       THEN 'Before' ELSE 'After' END AS phase,
  AVG(decision_dt::date - request_dt::date) AS avg_turnaround_days
FROM healthcare_ba.authorizations
WHERE decision_dt IS NOT NULL
  AND decision_status IN ('APPROVED','DENIED')
GROUP BY phase
ORDER BY phase;

-- HEDIS Compliance Rate (Monthly %)
SELECT
  he.measurement_month,
  he.measure_id,
  COUNT(DISTINCT CASE WHEN e.event_dt BETWEEN he.measurement_month
                       AND (he.measurement_month + INTERVAL '1 month' - INTERVAL '1 day')
                      THEN he.member_id END) AS numerator,
  COUNT(DISTINCT he.member_id) AS denominator,
  ROUND(100.0 *
        COUNT(DISTINCT CASE WHEN e.event_dt BETWEEN he.measurement_month
                               AND (he.measurement_month + INTERVAL '1 month' - INTERVAL '1 day')
                            THEN he.member_id END)::numeric
        / NULLIF(COUNT(DISTINCT he.member_id),0),2) AS compliance_pct
FROM healthcare_ba.hedis_eligibility he
LEFT JOIN healthcare_ba.hedis_events e
       ON e.member_id = he.member_id
      AND e.measure_id = he.measure_id
GROUP BY he.measurement_month, he.measure_id
ORDER BY he.measurement_month;
