# US Airline Route and Fare Analysis Using DOT DB1B Data

## Project Overview
This project analyses US domestic airline fare patterns using the DOT DB1B Origin and Destination Survey dataset. The goal is to identify how route distance, carrier, passenger volume, quarter, and market characteristics influence average fares, then build a regression model to predict market fare.

## Reference Project
This project was inspired by a beginner flight price prediction workflow from tkarim45's GitHub repository. However, instead of using a pre-cleaned Kaggle airline dataset, this project applies a similar analytics and modelling workflow to the US DOT DB1B dataset.

## Dataset
The DOT DB1B Origin and Destination Survey is a 10% sample of airline tickets from reporting carriers. The Market table contains directional origin-destination market records with information such as origin, destination, passengers, fares, distances, and carrier details.

## Understanding `MktFare` (Important Caveat)

The target variable `MktFare` is the **reported market fare** for a DB1B market record. It reflects real pricing data, but it does **not always equal the full cash price a customer paid for a standalone flight**.

Important nuances:

- **Market-level, not always ticket-level:** DB1B stores fares at the origin–destination market level. On multi-segment trips (`MktCoupons > 1`), the total ticket fare can be **prorated across segments**, so one market may show a very low fare (e.g. $5.50) even when the full itinerary cost much more.
- **Very low fares are often non-standard:** Extremely low values (such as `$5.00` or `$5.50`) frequently appear on long-distance routes and are likely special or allocated fares (for example award travel, companion tickets, or reporting/proration effects), not typical paid economy prices.
- **What this project predicts:** The model aims to predict **expected reported market fare** in DB1B based on route, carrier, distance, and demand characteristics — not a live quote from an airline booking site.

Cleaning approach used to improve interpretability:

- Remove invalid fares/distances (`MktFare <= 0`, `MktMilesFlown <= 0`)
- Exclude bulk fares where appropriate (`BulkFare == 0`)
- Focus on simpler itineraries where possible (`MktCoupons == 1`)
- Trim extreme fare outliers (e.g. 1st–99th percentile) before modelling

## Business Questions
1. Which US airline routes have the highest and lowest average fares?
2. Which routes carry the most passengers?
3. How does fare vary by distance group?
4. Which carriers have higher average fares?
5. Are high-volume routes cheaper or more expensive?
6. Can market fare be predicted using route, carrier, distance, passenger volume, and quarter?

## Tools Used
- Python
- pandas
- NumPy
- matplotlib
- seaborn
- scikit-learn
- Power BI
- Cursor

## Project Workflow
1. Data understanding
2. Data cleaning
3. Exploratory data analysis
4. Feature engineering
5. Regression modelling
6. Model evaluation
7. Dashboard creation
8. Business insight summary

## Key Insights
To be added after analysis.

## Model Performance
| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | TBD | TBD | TBD |
| Random Forest | TBD | TBD | TBD |
| Gradient Boosting | TBD | TBD | TBD |

## Dashboard Preview
Add dashboard screenshots here.

## Conclusion
This project demonstrates route-level fare analysis, real-world data cleaning, feature engineering, regression modelling, and dashboard storytelling using a public aviation dataset.
