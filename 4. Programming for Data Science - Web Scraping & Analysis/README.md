# NOVA IMS Teaching Staff — Web Scraping & Data Analysis

## 📌 Overview
- **Course:** Programming for Data Science — NOVA IMS (2024/25)  
- **Type:** Group project  
- **Goal:** Reconstruct a deleted data pipeline by scraping the **NOVA IMS teaching staff page**, wrangle the resulting dataset, and generate meaningful insights using Python.  
- **Deliverables:** Jupyter Notebook, cleaned dataset (`nova_ims_teaching_staff_2024-12-20.csv`), final presentation/report.  

This project demonstrates the full data science workflow: **web scraping → preprocessing → exploratory data analysis → advanced methods**.

---

## 📊 Dataset
- **Source:** [NOVA IMS Teaching Staff](https://www.novaims.unl.pt/en/nova-ims/teaching-staff/)  
- **Content:** Information about professors, courses, publications, and biographies.  
- **Pipeline Objective:** Automatically scrape and replicate the dataset structure, including additional information accessible via “Know more >”.  
- **Included:** The cleaned dataset (`nova_ims_teaching_staff_2024-12-20.csv`) is stored in this repository.  
 
---

## 🧹 Data Wrangling & Analysis
Main preprocessing and exploration steps:
1. Treated **missing values** and **duplicates** (with justification).  
2. Computed teacher statistics:  
   - Top-1 by **word count** (biography length)  
   - Top-5 by **course count**  
   - Top-10 by **publications**  
3. Analyzed **distributions and correlations** between word count, course count, and publications.  
4. Compared variables across **teacher types** (associate, assistant, invited, etc.).  
5. Extracted structural insights:  
   - Number of **unique courses**  
   - Courses taught by only one professor  
   - Probability of co-teaching (e.g., “Data Mining I” and “Data Mining II”)  
6. Added at least **3 additional insights** chosen by the group.  

---

## 🧠 Data Science in Action
Applied more advanced techniques beyond descriptive analysis:
- **Regression/Decision Tree** to predict **number of publications** or **teacher type**.  
- **Feature importance visualization** to explain model behavior.  
- **Text mining** on biographies to identify common terms in highly published or multi-course professors (e.g., word clouds).  
- **Association rule mining** to identify which courses are likely to be taught together, measuring confidence, lift, and support.  

---

## 📈 Results & Insights
- Built a functioning **web scraping pipeline** to regenerate the dataset.  
- Found clear patterns in **course distribution** and **professor specialization**.  
- Showed correlations between **biography length, number of courses, and publications**.  
- Discovered interesting **co-teaching patterns** (e.g., “Data Mining I” ↔ “Data Mining II”).  
- Validated feasibility of simple predictive models for **publications** and **teacher classification**.  

---

## 🧠 Key Learnings
- Learned how to combine **web scraping** with **data wrangling** for real-world datasets.  
- Understood challenges of **data cleaning** (duplicates, normalization, missing values).  
- Practiced **EDA, predictive modeling, and association rules** in a structured workflow.  
- Gained experience in documenting and presenting results effectively.  

