# Day 6: January 3, 2026 - BigQuery ML Advanced: Forecasting and Challenge Lab

## Overview
Today completes BigQuery ML with time series forecasting, recommendation systems, and a challenge lab.

## Exam Section Coverage
- **Section 1.1**: Developing ML models by using BigQuery ML (forecasting, matrix factorization)
- **Section 1.1**: Feature engineering or selection using BigQuery ML
- **Section 1.1**: Generating predictions by using BigQuery ML

## Time Estimate: ~3 hours

---

## Course: Create ML Models with BigQuery ML (Continued)

**Course Link**: [Create ML Models with BigQuery ML](https://www.skills.google/paths/17/course_templates/626)

Complete Labs 3-5 today:

---

### Lab 3: Predict Taxi Fare with a BigQuery ML Forecasting Model

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Predict Taxi Fare with a BigQuery ML Forecasting Model | 20 min | [Start Lab](https://www.skills.google/paths/17/course_templates/626/labs/612210) |

**Description**: In this lab, you explore millions of New York City yellow taxi cab trips available in a BigQuery Public Dataset, create a machine learning model inside of BigQuery to predict the fare, and evaluate the performance of your model to make predictions.

**What you'll learn:**
- Time series forecasting with ARIMA_PLUS
- Feature engineering for time-based data
- Regression model comparison
- Model evaluation for forecasting

**Time Series Model Creation:**
```sql
CREATE OR REPLACE MODEL `dataset.taxi_forecast`
OPTIONS(
  model_type='ARIMA_PLUS',
  time_series_timestamp_col='pickup_datetime',
  time_series_data_col='fare_amount',
  auto_arima=TRUE,
  data_frequency='DAILY'
) AS
SELECT
  DATE(pickup_datetime) as pickup_datetime,
  SUM(fare_amount) as fare_amount
FROM `dataset.taxi_trips`
GROUP BY 1;
```

**Forecasting:**
```sql
SELECT * FROM ML.FORECAST(MODEL `dataset.taxi_forecast`,
  STRUCT(30 AS horizon, 0.9 AS confidence_level));
```

---

### Lab 4: Bracketology with Google Machine Learning

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Bracketology with Google Machine Learning | 20 min | [Start Lab](https://www.skills.google/paths/17/course_templates/626/labs/612211) |

**Description**: In this lab, you use BigQuery to analyze the public NCAA dataset and BigQuery ML to predict NCAA tournament brackets.

**What you'll learn:**
- Build prediction models for real-world scenarios
- Feature engineering for sports analytics
- Model comparison and selection
- Handling imbalanced datasets

**Key skills:**
- [ ] Creative feature engineering
- [ ] Domain-specific model building
- [ ] Practical ML application

---

### Lab 5: Create ML Models with BigQuery ML - Challenge Lab

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Create ML Models with BigQuery ML: Challenge Lab | 20 min | [Start Lab](https://www.skills.google/paths/17/course_templates/626/labs/612212) |

**Description**: This challenge lab tests your skills in developing and using machine learning models using BigQuery.

**Challenge objectives:**
- Demonstrate BigQuery ML proficiency
- Build appropriate model types
- Perform feature engineering
- Evaluate and compare models
- Generate predictions

**Preparation checklist:**
- [ ] Review all BQML model types
- [ ] Practice CREATE MODEL syntax
- [ ] Know evaluation functions (ML.EVALUATE)
- [ ] Understand prediction functions (ML.PREDICT, ML.FORECAST)

---

## BigQuery ML Feature Engineering

### Common Transformations

```sql
-- Bucketizing continuous features
ML.BUCKETIZE(age, [0, 18, 35, 50, 65, 100]) AS age_bucket

-- Feature crosses
ML.FEATURE_CROSS(STRUCT(category1, category2)) AS cross_feature

-- Polynomial features
POWER(feature, 2) AS feature_squared

-- Date/time features
EXTRACT(DAYOFWEEK FROM timestamp) AS day_of_week,
EXTRACT(HOUR FROM timestamp) AS hour
```

### TRANSFORM Clause
```sql
CREATE MODEL `dataset.model`
TRANSFORM(
  ML.BUCKETIZE(age, [18, 35, 50, 65]) AS age_bucket,
  ML.STANDARD_SCALER(income) OVER() AS scaled_income,
  * EXCEPT(age, income)
)
OPTIONS(model_type='logistic_reg')
AS SELECT * FROM training_data;
```

---

## BigQuery ML Functions Reference

| Function | Purpose |
|----------|---------|
| `ML.EVALUATE` | Get model evaluation metrics |
| `ML.PREDICT` | Make predictions |
| `ML.FORECAST` | Time series forecasting |
| `ML.EXPLAIN_PREDICT` | Get prediction explanations |
| `ML.FEATURE_INFO` | Get feature importance |
| `ML.WEIGHTS` | Get model weights |
| `ML.TRAINING_INFO` | Get training statistics |
| `ML.CONFUSION_MATRIX` | Get confusion matrix |
| `ML.ROC_CURVE` | Get ROC curve data |

---

## End of Day Checklist

- [ ] Completed: Predict Taxi Fare lab (20 min)
- [ ] Completed: Bracketology lab (20 min)
- [ ] Completed: Challenge Lab (20 min)
- [ ] Mastered BigQuery ML feature engineering
- [ ] Know all BigQuery ML model types and functions

---

## Week 1 Summary

**Courses completed:**
1. Introduction to AI and Machine Learning on Google Cloud
2. Introduction to Generative AI
3. Introduction to Large Language Models
4. Prepare Data for ML APIs on Google Cloud
5. Working with Notebooks in Vertex AI
6. Create ML Models with BigQuery ML

**Key skills gained:**
- Google Cloud AI/ML foundations
- Data processing with Dataflow, Dataprep
- Pre-trained APIs (Vision, NLP, Speech, Video)
- Notebook development environments
- BigQuery ML model building and feature engineering

---

## Notes Section
*Use this space for your own notes during study:*




---

## Weekend Break
Enjoy January 4-5 off! Day 7 (January 6th) covers [Engineer Data for Predictive Modeling with BigQuery ML](https://www.skills.google/paths/17/course_templates/627).
