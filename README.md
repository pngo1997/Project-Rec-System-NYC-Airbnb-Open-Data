# 🏗️ New York City Airbnb Recommendation System  

## 📜 Overview  
This project develops a **content-based recommendation system** for **New York City Airbnb listings**, utilizing **Airbnb Open Data, customer reviews, and NYC subway station locations**. The system helps users find the most suitable Airbnb listings based on their preferences for **neighborhood, price point, and review rating**. The recommendation includes the nearest subway station and distance for convenience.  

## 🎯 Problem Explanation  

### **Datasets Used**  
The project incorporates three datasets:  
1. **NYC Airbnb Listings** (42,931 observations) – Airbnb listing details such as location, price, and availability.  
2. **NYC Airbnb Reviews** (1,110,024 observations) – Customer reviews for sentiment analysis.  
3. **NYC Subway Stations** (473 observations) – Subway locations for accessibility recommendations.  

The goal is to preprocess these datasets, extract meaningful features, and **build a recommendation system**.  

## 🛠️ Implementation Details  

### **1. Data Preprocessing**  
- **Exploratory Data Analysis (EDA)**  
  - Histograms, scatterplots, and geospatial maps used to visualize distributions and relationships between features.  
  - Identification of high-priced listings and popular Airbnb neighborhoods.  
  - Outlier detection and removal.  

- **Sentiment Analysis for Review Scores**  
  - Applied **RoBERTa (Robustly Optimized BERT Approach)**, a **pre-trained NLP model**, to analyze review sentiment.  
  - Generated **compound sentiment scores** (scaled **1 to 5**) for use in recommendations.  

- **Clustering Airbnb Listing Names**  
  - Used **TF-IDF** and **K-Means clustering** to group listings based on descriptive text.  
  - Determined **9 optimal clusters** via the **Elbow method**.  

- **Calculating Nearest Subway Station**  
  - Used **Geopy’s geodesic distance function** to compute distances between each Airbnb and its nearest subway station.  
  - Stored **nearest subway station name and distance (in miles)** as features.  

### **2. Recommendation System Development**  
- **Content-Based Filtering Approach**  
  - Users provide **three preferences**:  
    1. **Neighborhood Group** (e.g., Manhattan, Brooklyn)  
    2. **Maximum Price**  
    3. **Minimum Review Rating**  
  - Filters Airbnb listings based on user inputs.  
  - Uses **Cosine Similarity** to compare user preferences with listing features.  
  - Returns **top five most relevant listings** along with:  
    - Listing Name  
    - Neighborhood  
    - Review Score  
    - Nearest Subway Station & Distance  

### **3. Evaluation Metrics**  
- **Explored Review Score Effectiveness**  
  - Compared **RoBERTa-generated sentiment scores** against raw reviews.  
- **Evaluated K-Means Clustering Performance**  
  - Used **Elbow method** to select the best number of clusters.  
- **Validated Recommendation Quality**  
  - Ensured recommendations align with user preferences.  

## 🚀 Technologies Used  
- **Python** (for data processing and modeling).  
- **Pandas & NumPy** (for data handling and transformation).  
- **Scikit-learn** (for TF-IDF, K-Means clustering, and similarity computation).  
- **NLTK & Transformers (Hugging Face)** (for NLP-based review sentiment analysis).  
- **Geopy** (for distance calculations).  
- **Matplotlib & Seaborn** (for visualization).  

## 📊 Example Output  

### **Top 5 Recommended Listings Based on User Preferences**
#### User Input:
- Neighborhood: Brooklyn
- Max Price: $150
- Minimum Review Score: 4.0

#### Recommended Listings:
1. Cozy Studio in Williamsburg
- Review Score: 4.7
- Price: $140
- Nearest Subway: Bedford Ave (0.3 miles)
2. Bright Apartment in Bushwick
- Review Score: 4.5
- Price: $135
- Nearest Subway: Jefferson St (0.5 miles)
3. Quiet Retreat near Prospect Park
- Review Score: 4.6
- Price: $120
- Nearest Subway: Parkside Ave (0.2 miles)
4. Budget-Friendly Stay in Greenpoint
- Review Score: 4.3
- Price: $110
- Nearest Subway: Greenpoint Ave (0.4 miles)
5. Loft-Style Apartment in DUMBO
- Review Score: 4.8
- Price: $149
- Nearest Subway: York St (0.3 miles)
