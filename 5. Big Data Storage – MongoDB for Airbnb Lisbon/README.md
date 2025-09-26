# 🏙️ Big Data Storage — MongoDB Airbnb Lisbon Analysis

## 📌 Overview
This project explores the use of **MongoDB Atlas** to store, query, and analyze Airbnb data from Lisbon.  
Due to storage limitations in the free tier, the original raw datasets (several hundred MBs) were **cropped** and pre-processed before being uploaded.  

The work includes:  
- Data ingestion into MongoDB collections  
- Schema validation rules to ensure data quality  
- Index creation for optimized query performance  
- Aggregation pipelines for insights extraction  
- Final presentation and report  

---

## 📊 Dataset
- **Source:** [Inside Airbnb — Get the Data](https://insideairbnb.com/get-the-data/)  
- **City:** Lisbon  
- **Original files:**  
  - `calendar.csv`  
  - `listings.csv` 
  - `reviews.csv` 
  - `neighbourhoods.csv` + `neighbourhoods.geojson`  
  - `hosts.csv`  

Due to size constraints, only the **cropped and cleaned versions** were uploaded in this repository (`hosts_fixed.csv`, `listings_fixed_hosts_deleted_price_fixed.csv`, `listings_strange_pricing_deleted.csv`).  

---

## ⚙️ Key Steps
1. **Data preparation**  
   - Cropping and cleaning large CSV files to meet Atlas limits  
   - Exporting data to BSON for import into MongoDB  

2. **Database setup**  
   - Uploading data into MongoDB collections  
   - Defining **validation rules** for schema consistency  

3. **Performance optimization**  
   - Creating indexes to improve query efficiency  
   - Running aggregation pipelines for insights  

4. **Results & Reporting**  
   - All queries, results, and conclusions documented in the final report and presentation  

---

## 🎯 Key Learnings
- Hands-on experience with **MongoDB Atlas** and data modeling  
- Importance of **data preprocessing** when handling large-scale datasets  
- How **indexes and validation** affect query performance and data quality  
- Using **aggregation pipelines** for complex analytical queries  

---

## 📖 References
- [Inside Airbnb — Lisbon datasets](https://insideairbnb.com/get-the-data/)  
- MongoDB Documentation: [https://www.mongodb.com/docs/](https://www.mongodb.com/docs/)
