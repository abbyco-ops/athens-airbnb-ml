# What Drives Airbnb Occupancy in Athens?
*A supervised machine learning analysis on short-term rental listings in Athens, Greece*

**View the full interactive report ->** https://abbyco-ops.github.io/athens-airbnb-ml/

## Overview
Athens is one of Europe's most visited cities, and its Airbnb market is highly competitive, with thousands of active listings. 
This project asks: what actually drives a listing toward high occupancy?

I framed this as a binary classication problem, predicitng whether a listing falls into **High Occupancy** or **Low Occupancy** (defined by below- vs. above- median annual availability), and trained eight supervised learning models to find out which listing characteristics matter most.

## Data
* **Data Source:** Inside Airbnb. (2025, September 26). Athens, Attica, Greece listings data [Data set]. Retrieved from https://insideairbnb.com/get-the-data/
* **Size:** 14,524 listings after cleaning, 12 predictors
* **Outcome:** high_occupancy, derived from availability_365 (below-median availability = high occupancy)

## Approach
1. **Exploratory Data Analysis: examined how price, room type, reviews, host status, and capacity relate to occupancy
2. **Train/test split** (80/20 stratified) with **5-fold cross validation** for model tuning
3. **Eight models compared:** Logistic Regression, Pruned Decisio Tree, Lasso, Elastic Net, KNN, LDA, QDA, and Random Forest
4. **Model selection** via ROC AUC, with the winner evaluated on a held-out test set
5. **Variable importance** analysis on the final model

## Results
The **Random Forest** was the best model, generalizing well to the test set (ROC AUC 0.674, accuracy 0.623).

## Key Finding
**Price matters far more than capacity**. price and price_per_person dominate the Random Forest's variable importance rankings, well ahead of review volume/rating, and group-size features (beds, accommodates, bedrooms) rank in the middle. For hosts in Athens, competitive pricing appears to be a stronger lever for occupancy than adding capacity.

## Limitations
* availability_365 is an imperfect proxy for occupancy — hosts can block dates for personal reasons unrelated to demand, which adds noise to the labels and likely suppresses model performance across the board.
* The dataset lacks booking history or revenue data, which would more directly capture demand.
* Findings are specific to the Athens market as of the September 2025 snapshot.

## Repository Structure
```
.
├── index.Rmd       # Full analysis: EDA, modeling, evaluation, appendix
├── index.html      # Rendered report (published via GitHub Pages)
├── images/         # Photos used in the report
│   ├── Athens_Aura.JPG
│   └── Acropolis.jpeg
└── FinalProject.Rproj
```

## Author
**Abigaile Co** UCSB, Spring 2026
