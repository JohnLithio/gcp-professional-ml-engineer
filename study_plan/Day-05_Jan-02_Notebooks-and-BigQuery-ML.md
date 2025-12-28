# Day 5: January 2, 2026 - Working with Notebooks and BigQuery ML

## Overview
Today covers Jupyter notebooks in Vertex AI and begins BigQuery ML for low-code ML development.

## Exam Section Coverage
- **Section 1.1**: Developing ML models by using BigQuery ML
- **Section 2.2**: Model prototyping using Jupyter notebooks

## Time Estimate: ~5 hours

---

## Course 1: Working with Notebooks in Vertex AI

**Course Link**: [Working with Notebooks in Vertex AI](https://www.skills.google/paths/17/course_templates/923)

---

### Module: Notebook Solutions on Vertex AI

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Working with Notebooks in Vertex AI | <1 min | [Watch](https://www.skills.google/paths/17/course_templates/923/video/613492) |
| Video | Vertex AI Notebook Solutions | 6 min | [Watch](https://www.skills.google/paths/17/course_templates/923/video/613493) |
| Video | Vertex AI Colab Enterprise notebooks | 6 min | [Watch](https://www.skills.google/paths/17/course_templates/923/video/613494) |
| Video | Vertex AI Workbench instances notebooks | 10 min | [Watch](https://www.skills.google/paths/17/course_templates/923/video/613495) |
| Video | Summary | 3 min | [Watch](https://www.skills.google/paths/17/course_templates/923/video/613496) |
| Quiz | Working with Notebooks in Vertex AI: Quiz | 15 min | [Take Quiz](https://www.skills.google/paths/17/course_templates/923/quizzes/613497) |
| Lab | Exploratory Data Analysis using BigQuery and Colab Enterprise | 2 hrs | [Start Lab](https://www.skills.google/paths/17/course_templates/923/labs/613498) |
| Lab | Exploratory Data Analysis using BigQuery and Workbench Instances | 2 hrs | [Start Lab](https://www.skills.google/paths/17/course_templates/923/labs/613499) |

**Choose ONE lab based on your preference:**
- **Colab Enterprise Lab**: Better for serverless, collaborative work
- **Workbench Instances Lab**: Better for custom environments with persistent storage

---

### Key Notebook Concepts

**Backend comparison:**
| Feature | Vertex AI Workbench | Colab Enterprise |
|---------|---------------------|------------------|
| Best for | Full data science workflow | Serverless, collaborative |
| GPU Support | Yes | Yes |
| Managed | Fully managed VMs | Serverless |
| Persistence | Persistent disk | Ephemeral by default |

**Security best practices:**
- VPC Service Controls for network isolation
- Customer-managed encryption keys (CMEK)
- Service account configuration for least privilege
- IAM roles: `roles/notebooks.admin`, `roles/notebooks.viewer`, `roles/notebooks.runner`

---

## Course 2: Create ML Models with BigQuery ML

**Course Link**: [Create ML Models with BigQuery ML](https://www.skills.google/paths/17/course_templates/626)

Complete Labs 1-2 today:

---

### Lab 1: Getting Started with BigQuery ML

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Getting Started with BigQuery ML | 20 min | [Start Lab](https://www.skills.google/paths/17/course_templates/626/labs/612208) |

**Description**: In this lab, you learn how to use BigQuery to create a machine learning model that predicts whether a visitor will make a transaction.

**What you'll learn:**
- Create ML models using SQL
- Understand BQML model types
- Train and evaluate models
- Make predictions

**Key SQL patterns:**
```sql
-- Create a model
CREATE OR REPLACE MODEL `dataset.model_name`
OPTIONS(
  model_type='logistic_reg',
  input_label_cols=['label']
) AS
SELECT * FROM `dataset.training_data`;

-- Evaluate the model
SELECT * FROM ML.EVALUATE(MODEL `dataset.model_name`);

-- Make predictions
SELECT * FROM ML.PREDICT(MODEL `dataset.model_name`,
  (SELECT * FROM `dataset.new_data`));
```

---

### Lab 2: Predict Visitor Purchases with a Classification Model

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Predict Visitor Purchases with a Classification Model in BigQuery ML | 25 min | [Start Lab](https://www.skills.google/paths/17/course_templates/626/labs/612209) |

**Description**: In this lab, you use an available ecommerce dataset to create a classification (logistic regression) model in BigQuery ML that predicts customers' purchasing habits.

**Classification metrics to understand:**
| Metric | Description |
|--------|-------------|
| Accuracy | Overall correct predictions |
| Precision | True positives / Predicted positives |
| Recall | True positives / Actual positives |
| F1-Score | Harmonic mean of precision and recall |
| AUC-ROC | Area under ROC curve |

---

## BigQuery ML Model Types

| Model Type | Use Case | SQL Keyword |
|------------|----------|-------------|
| Linear Regression | Predict continuous values | `linear_reg` |
| Logistic Regression | Binary classification | `logistic_reg` |
| K-means Clustering | Unsupervised grouping | `kmeans` |
| Matrix Factorization | Recommendations | `matrix_factorization` |
| Time Series (ARIMA) | Forecasting | `arima_plus` |
| Boosted Trees | Classification/Regression | `boosted_tree_classifier/regressor` |
| DNN | Deep learning | `dnn_classifier/regressor` |
| AutoML Tables | Automatic model selection | `automl_classifier/regressor` |

---

## End of Day Checklist

### Working with Notebooks
- [ ] Watched: Working with Notebooks in Vertex AI (<1 min)
- [ ] Watched: Vertex AI Notebook Solutions (6 min)
- [ ] Watched: Vertex AI Colab Enterprise notebooks (6 min)
- [ ] Watched: Vertex AI Workbench instances notebooks (10 min)
- [ ] Watched: Summary (3 min)
- [ ] Passed: Working with Notebooks Quiz
- [ ] Completed: EDA Lab (choose Colab Enterprise OR Workbench)

### BigQuery ML
- [ ] Completed: Getting Started with BigQuery ML lab (20 min)
- [ ] Completed: Predict Visitor Purchases lab (25 min)
- [ ] Understand BigQuery ML model types and syntax

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 6 completes [BigQuery ML](https://www.skills.google/paths/17/course_templates/626) with forecasting models and the challenge lab.
