# Customer Targeting & Product Recommendation System

A data-driven customer analytics and product recommendation system built using Python, pandas, NumPy, scikit-learn, and association-rule techniques.

The project analyzes customer purchasing behavior, assigns customer segments based on RFM and customer value scoring, identifies actionable customer groups, and generates personalized product recommendations using historical co-purchase behavior.

---

## Project Overview

Understanding customer behavior is important for targeted marketing, customer retention, and personalized product recommendations.

This project combines customer-level analytics with a recommendation approach to answer questions such as:

- Which customers are the most valuable?
- Which customers are becoming inactive?
- Which customers have high growth potential?
- Which customers can be targeted for cross-selling?
- Which products are commonly purchased together?
- How well does the recommendation system perform on unseen transactions?

The project follows a complete analytics workflow from data cleaning and customer analysis to segmentation, recommendation generation, and model evaluation.

---

## Objectives

The main objectives of this project are to:

- Analyze customer purchasing behavior
- Perform RFM-based customer analysis
- Develop a customer value scoring system
- Segment customers into actionable groups
- Generate business recommendations for each segment
- Identify products frequently purchased together
- Build a product recommendation system
- Evaluate recommendation performance using historical transactions
- Compare recommendation approaches using Hit Rate, Recall, and Coverage

---

## Dataset

The project uses a retail transaction dataset containing transactional-level customer purchase information.

### Main Features

| Column | Description |
|---|---|
| InvoiceNo | Transaction/invoice identifier |
| StockCode | Product identifier |
| Description | Product description |
| Quantity | Number of units purchased |
| InvoiceDate | Transaction date and time |
| UnitPrice | Price per unit |
| CustomerID | Customer identifier |
| Country | Customer's country |

The dataset contains more than 500,000 transaction records and thousands of customers and products before preprocessing.

> The raw dataset is not included in this repository.

---

## Project Workflow

```text
Raw Transaction Data
        ↓
Data Understanding
        ↓
Data Quality Assessment
        ↓
Data Cleaning & Preprocessing
        ↓
Revenue Analysis
        ↓
Customer-Level Metrics
        ↓
RFM Analysis
        ↓
Customer Value Scoring
        ↓
Customer Segmentation
        ↓
Business Insights & Actions
        ↓
Product Co-Purchase Analysis
        ↓
Association-Based Recommendations
        ↓
Train/Test Evaluation
        ↓
Popularity Fallback
        ↓
Final Recommendation Model

---

## RFM Analysis

Customer purchasing behavior is analyzed using three key dimensions:

- **Recency:** How recently a customer made a purchase
- **Frequency:** How frequently a customer makes transactions
- **Monetary:** How much revenue a customer generates

RFM scores are calculated using quintile-based scoring. Recency is scored in reverse order so that more recent customers receive higher scores, while higher frequency and monetary values receive higher scores.

---

## Customer Value Scoring

A Customer Value Score is developed to combine the three major dimensions of customer behavior.

The scoring framework uses:

| Component | Weight |
|---|---:|
| Recency | 40% |
| Frequency | 30% |
| Monetary | 30% |

Frequency and Monetary values are log-transformed before normalization to reduce the effect of highly skewed values.

The resulting Customer Value Score is used to rank customers based on their overall value.

---

## Customer Segmentation

Customers are assigned to actionable segments using RFM scores and Customer Value Score.

The project identifies five customer segments:

| Segment | Business Focus |
|---|---|
| VIP / Loyal | Retain & Reward |
| High Potential | Upsell & Loyalty Program |
| Active - Cross Sell | Cross-Sell Products |
| High Value - Win Back | Win-Back Campaign |
| Nurture | Re-Engagement / Nurture |

This segmentation transforms customer-level behavioral data into actionable business groups.

---

## Business Insights & Customer Actions

Each segment is connected with a recommended business action.

### VIP / Loyal
Customers showing strong recent activity, purchase frequency, and monetary value.

**Action:** Retain & Reward

### High Potential
Customers with strong overall customer value who represent an opportunity for further growth.

**Action:** Upsell & Loyalty Program

### Active - Cross Sell
Recently active customers who can be targeted with relevant additional products.

**Action:** Cross-Sell Products

### High Value - Win Back
Previously valuable customers whose recent purchasing activity has declined.

**Action:** Win-Back Campaign

### Nurture
Customers with comparatively lower engagement or value.

**Action:** Re-Engagement / Nurture

---

## Product Recommendation System

The project also includes a product recommendation component based on historical customer-product purchasing behavior.

The recommendation workflow includes:

1. Customer-product interaction analysis
2. Product popularity analysis
3. Co-purchase relationship analysis
4. Association-based recommendation generation
5. Train/test evaluation
6. Popularity-based fallback recommendations

The system uses products previously purchased by a customer to identify related products that can be recommended based on learned product relationships.

---

## Recommendation Evaluation

The recommendation system is evaluated using a time-based train/test approach.

Historical transactions are used to build the recommendation model, while later transactions are used to evaluate recommendations on unseen customer purchases.

The following metrics are used:

### Hit Rate@5

Measures the percentage of evaluated customers for whom at least one recommended product appears in their test purchases.

### Recall@5

Measures how much of the customer's relevant test purchases are captured by the top-5 recommendations.

### Coverage@5

Measures the percentage of customers for whom the system generates at least one recommendation.

---

## Recommendation Models

Two recommendation approaches are evaluated:

### Baseline Association Rules

Generates product recommendations using association relationships learned from training transactions.

### Association + Popularity Fallback

Uses association-based recommendations when available and falls back to popular products when sufficient association-based recommendations cannot be generated.

This approach allows the system to provide recommendations to a broader set of customers.

---

## Model Comparison

The notebook generates a model comparison table using the actual evaluation results.

The comparison includes:

| Model | Hit Rate@5 | Recall@5 | Coverage@5 |
|---|---:|---:|---:|
| Baseline Association Rules | Calculated in notebook | Calculated in notebook | Calculated in notebook |
| Association + Popularity Fallback | Calculated in notebook | Calculated in notebook | Calculated in notebook |

The metrics are calculated dynamically from the evaluation results rather than being manually entered.

---

## Key Project Outcomes

The project produces several customer and product analytics outputs:

- Customer-level RFM metrics
- Customer Value Scores
- Customer rankings
- Customer segments
- Segment-level business insights
- Recommended customer actions
- Product recommendation rules
- Recommendation evaluation metrics
- Final recommendation examples

---

## Technologies Used

- **Python**
- **Pandas**
- **NumPy**
- **Scikit-learn**
- **SciPy**
- **Matplotlib**
- **Jupyter Notebook**
- **Google Colab**

---

## Project Structure

```text
customer-targeting-recommendation-system/
│
├── Customer_Targeting_Recommendation_System.ipynb
├── README.md
├── .gitignore
│
└── outputs/
    ├── model_comparison.csv
    ├── recommendation_rules.csv
    └── final_recommendations.csv

## How to Run
###1. Clone the Repository
git clone https://github.com/yourusername/customer-targeting-recommendation-system.git
###2. Open the Notebook

Open:

Customer_Targeting_Recommendation_System.ipynb

using Jupyter Notebook or Google Colab.

###3. Dataset

The raw dataset is not included in this repository.

The notebook is configured to load the dataset from Google Drive when running in Google Colab.

Update the dataset path if necessary:

PROJECT_PATH = "/content/drive/MyDrive/Customer_Targeting_Recommendation_System"
###4. Run the Notebook

Run the notebook cells sequentially from data loading through recommendation evaluation.

##Outputs

The project generates the following output files:

model_comparison.csv

Contains the evaluation comparison of recommendation approaches.

recommendation_rules.csv

Contains the learned recommendation relationships used by the recommendation system.

final_recommendations.csv

Contains generated product recommendations for selected customers.

##Future Improvements

The current system can be extended with:

-Collaborative filtering
-Matrix factorization
-Content-based recommendation
-Hybrid recommendation models
-More advanced ranking techniques
-Time-aware recommendation models
-Automated customer targeting
-Interactive recommendation interface
-Model monitoring and periodic retraining
##Disclaimer

This project is developed for learning, portfolio, and analytical demonstration purposes.

The recommendation results are based on historical transaction behavior and should be interpreted as analytical recommendations rather than guaranteed future purchasing behavior.

##Author

Raqiqa Zafar

Data Analytics | Python | SQL | Power BI | Excel

GitHub: https://github.com/Raqiqazafar

LinkedIn: https://linkedin.com/in/raqiqa-zafar
