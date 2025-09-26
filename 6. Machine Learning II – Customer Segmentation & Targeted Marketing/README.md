# Machine Learning II – Customer Segmentation
NOVA IMS · Data Science Degree · Group 61

## Project Overview
In today’s competitive market, customer segmentation is essential to unlock business growth and improve loyalty.  
This project applies **unsupervised machine learning** to identify distinct customer groups based on demographics, purchasing behavior, and transactional data.  

We combined clustering algorithms (K-Means, Hierarchical Clustering, DBSCAN) with association rule mining to deliver **8 meaningful segments** and propose **targeted marketing campaigns** tailored to each one.

---

## Datasets
We worked with two main datasets plus supporting files:

- `customer_info.csv` – demographic, geographic and lifetime spending behavior for each customer  
- `customer_basket.csv` – transactional data containing products purchased in each basket  
- `customer_info_preprocessed.csv` – cleaned dataset ready for clustering (after EDA, missing value imputation, outlier removal)  

---

## Methodology
1. **Exploratory Data Analysis & Preprocessing**  
   - Data cleaning and feature engineering (age, gender encoding, loyalty card handling)  
   - Missing values imputation and outlier removal (DBSCAN + thresholds)  
   - Geographic exploration to identify a distinct “Alfragide” segment  

2. **Customer Segmentation & Clustering**  
   - K-Means clustering with Elbow and Silhouette validation  
   - Hierarchical clustering to validate cluster topology  
   - Refinement with DBSCAN for ambiguous groups  
   - Dimensionality reduction with UMAP for visualization  
   - Final segmentation into **8 customer clusters**:
     - Tech-Savvy Buyers  
     - Vegetarians  
     - Large Family Households  
     - Young Promo-Sensitive  
     - High-Spending Shoppers  
     - Wide-Range Shoppers  
     - Promo-Oriented Seniors  
     - Alfragide (geo-based niche segment)

3. **Targeted Promotions via Association Rules**  
   - Mining of co-purchase patterns within each segment  
   - Translation into actionable marketing campaigns:
     - *Curated Experience Box*  
     - *Grill Essentials Kit*  
     - *Grocery + Game Combo*  
     - *Salad Builder*  
     - *Buy 2 Get 1 Free Happy Hour*  
     - *20% Off Petfood with Pantry Essentials*   
