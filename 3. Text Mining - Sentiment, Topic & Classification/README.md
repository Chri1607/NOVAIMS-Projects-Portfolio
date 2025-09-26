# Text Mining — Hyderabad Restaurant Reviews (Zomato)

## 📌 Overview
- **Course:** Text Mining — NOVA IMS (2024/25)  
- **Type:** Group project  
- **Goal:** Mine 10k Zomato reviews from Hyderabad to (1) predict **restaurant cuisines** from text (multi-label), (2) predict **rating polarity** (sentiment), and (3) extract **meal co-occurrences** and **topics** that describe the dining scene. :contentReference[oaicite:0]{index=0}

---

## 📊 Dataset
- **Scope:** 10,000 reviews for **100/105** restaurants in Hyderabad (May 2016–May 2019). Reviews average ~50 chars; rating distribution is skewed to 4–5 stars. Cuisines: **42** labels; each restaurant ~3 cuisines; a moderate positive correlation between **price** and **average rating**. :contentReference[oaicite:1]{index=1}

---

## 🧹 Preprocessing
- Removed empty/noisy reviews; normalized diacritics; standardized contractions; cleaned URLs/hashtags/newlines; optional tokenization/lemmatization/POS tagging depending on task. Spelling normalization and **gibberish filtering** (e.g., elongated tokens) reduced noise. :contentReference[oaicite:2]{index=2}  
- **Food NER:** extracted meal entities with a fine-tuned **RoBERTa** NER (InstaFoodRoBERTa), then lower-cased, deduplicated and filtered to get **7,197** distinct meals. :contentReference[oaicite:3]{index=3}  
- Built two corpora for modeling: **per-review** and **per-restaurant** (reviews aggregated). :contentReference[oaicite:4]{index=4}

---

## 🧠 Tasks & Methods

### 1) Sentiment Analysis
- Two approaches: **VADER** vs a **Transformer** (twitter-roberta-base-sentiment).  
- For sentiment data we **kept emojis/punctuation/stopwords** to preserve tone; mapped star ratings to {neg, neu, pos} for evaluation. :contentReference[oaicite:5]{index=5}

### 2) Multi-label Cuisine Classification
- Kept only reviews containing **food NER** to reduce noise; one-hot encoded 42 cuisines.  
- Vectorization: **TF-IDF**, **Bag-of-Words**, **Word2Vec** (tested).  
- Classifiers: **Logistic Regression**, **SVM**, **Random Forest** wrapped with **One-vs-Rest**, **Classifier Chains**, and **MultiOutput**. :contentReference[oaicite:6]{index=6}

### 3) Meal Co-occurrence & Clustering
- Cleaned/standardized dish names; merged synonyms (e.g., *biriyani*→*biryani*); removed non-dishes (ingredients only). Built a co-occurrence network on the **top 70** dishes for readability.  
- Clustering: (a) **HDBSCAN** on distance matrices from the co-occurrence graph; (b) **BERTopic** using transformer embeddings + **UMAP** + **HDBSCAN** with custom topic labels. :contentReference[oaicite:7]{index=7}

### 4) Topic Modeling
- **LDA (Gensim):** BoW with dictionary/corpus; grid over #topics/α/η.  
- **BERTopic:** embeddings + c-TF-IDF + MMR; hierarchical merge to **20** consolidated topics (ambience, service, delivery, cuisine types, desserts, veg, buffet, etc.). :contentReference[oaicite:8]{index=8}

---

## 📈 Results

### Sentiment
- **RoBERTa** outperforms VADER: **weighted F1 = 0.80** vs **0.73**; **Spearman ρ** with rating: **0.73** vs **0.57**. Mixed-polarity long reviews explain residual errors. :contentReference[oaicite:9]{index=9}

### Multi-label Cuisine
- Best setup: **Logistic Regression + MultiOutput**, **weighted F1 = 0.61** (42 labels). Strong on **North Indian, Lebanese, North-Eastern** (F1 > 0.70; North Indian ≈ 0.83); weaker on low-support cuisines (e.g., Japanese/Mexican). :contentReference[oaicite:10]{index=10}

### Meal Co-occurrence & Clustering
- **Biryani** is the central hub with the densest connections; “momos” and “shawarma” appear peripheral. Edges reveal cuisine bundles (e.g., **pasta–pizza–tiramisu** for Italian; **biryani** variants for Indian).  
- HDBSCAN with Pairwise distances reached **Silhouette ≈ 0.32** but clusters weren’t interpretable; **BERTopic** had lower **Silhouette ≈ 0.10** yet produced **clearer cuisine clusters**. :contentReference[oaicite:11]{index=11}

### Topics
- **LDA:** best at **14 topics**, **log_perplexity ≈ −936**, **coherence ~40%** → generic/overlapping topics.  
- **BERTopic:** ~**20** refined topics after hierarchical merge; largest shares: **place/ambience (~27%)**, **service (~17%)**, **delivery**, and **Biryani/Indian cuisine** prominence—consistent with the market. :contentReference[oaicite:12]{index=12}

---

## 💡 Insights
- Ratings align with **emotion composition** in text (anger ↔ low stars, joy ↔ high stars). :contentReference[oaicite:13]{index=13}  
- Cuisines with **ample support** are predictable from reviews; long-tail cuisines remain challenging. :contentReference[oaicite:14]{index=14}   
- Co-occurrence graphs surface **menu pairings** (e.g., Italian set-menus) and show **Indian staples (biryani)** as core to demand. :contentReference[oaicite:15]{index=15}

---

## 🧠 Key Learnings
- Careful **text cleaning + task-specific preprocessing** materially improves downstream models. :contentReference[oaicite:17]{index=17}  
- **Transformer sentiment** is robust on social-media-like reviews; lexicon baselines lag on mixed-polarity long texts. :contentReference[oaicite:18]{index=18}  
- For multi-label text, **simple linear models (LogReg)** with good features can beat heavier models under sparse labels. :contentReference[oaicite:19]{index=19}  
- **BERTopic** provides more **interpretable** structures than LDA on this corpus, despite lower intrinsic clustering scores. :contentReference[oaicite:20]{index=20}

---

## 📎 Reference
Full methodology, figures, and tables are documented in **Project report.pdf** in this folder. :contentReference[oaicite:21]{index=21}
