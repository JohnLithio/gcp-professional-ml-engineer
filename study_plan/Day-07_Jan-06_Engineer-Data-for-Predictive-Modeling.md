# Day 7: January 6, 2026 - Engineer Data for Predictive Modeling with BigQuery ML

## Overview
Today focuses on data engineering fundamentals for ML, including ETL pipelines, data transformation, and preparing data for BigQuery ML.

## Exam Section Coverage
- **Section 2.1**: Exploring and preprocessing organization-wide data
- **Section 2.1**: Data preprocessing (Dataflow, TFX, BigQuery)
- **Section 1.1**: Feature engineering using BigQuery ML

## Time Estimate: ~4 hours

---

## Course: Engineer Data for Predictive Modeling with BigQuery ML

**Course Link**: [Engineer Data for Predictive Modeling with BigQuery ML](https://www.skills.google/paths/17/course_templates/627)

This is a hands-on lab course. Complete all labs today.

---

### Lab 1: Creating a Data Transformation Pipeline with Cloud Dataprep

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Creating a Data Transformation Pipeline with Cloud Dataprep | 45 min | [Start Lab](https://www.skills.google/paths/17/course_templates/627/labs/612992) |

**Description**: Build visual data transformation pipelines, handle data quality issues, and create reusable transformation recipes.

**What you'll learn:**
- Build visual data transformation pipelines
- Handle data quality issues
- Create reusable transformation recipes
- Schedule pipeline execution

**Key transformation operations:**
| Operation | Use Case |
|-----------|----------|
| Filter | Remove unwanted rows |
| Derive | Create new columns |
| Aggregate | Group and summarize |
| Join | Combine datasets |
| Pivot | Reshape data |
| Unpivot | Normalize wide data |

---

### Lab 2: ETL Processing on Google Cloud Using Dataflow and BigQuery (Python)

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | ETL Processing on Google Cloud Using Dataflow and BigQuery (Python) | 1 hr | [Start Lab](https://www.skills.google/paths/17/course_templates/627/labs/612993) |

**Description**: In this lab, you build several data pipelines that ingest and transform data from a publicly available dataset into BigQuery.

**What you'll learn:**
- Build ETL pipelines with Apache Beam
- Read from various sources
- Transform data at scale
- Write to BigQuery

**ETL Pipeline Pattern:**
```python
import apache_beam as beam
from apache_beam.options.pipeline_options import PipelineOptions

def transform_data(element):
    # Your transformation logic
    return transformed_element

options = PipelineOptions([
    '--project=PROJECT_ID',
    '--runner=DataflowRunner',
    '--temp_location=gs://bucket/temp',
    '--region=us-central1'
])

with beam.Pipeline(options=options) as p:
    (p
     | 'Read' >> beam.io.ReadFromText('gs://bucket/input.csv')
     | 'Parse' >> beam.Map(parse_csv)
     | 'Transform' >> beam.Map(transform_data)
     | 'Filter' >> beam.Filter(lambda x: x['value'] > 0)
     | 'Write' >> beam.io.WriteToBigQuery(
         'project:dataset.table',
         schema='field1:STRING,field2:INTEGER',
         write_disposition=beam.io.BigQueryDisposition.WRITE_TRUNCATE
     ))
```

---

### Lab 3: Predict Visitor Purchases with a Classification Model in BigQuery ML

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Predict Visitor Purchases with a Classification Model in BigQuery ML | 25 min | [Start Lab](https://www.skills.google/paths/17/course_templates/627/labs/612994) |

**Description**: In this lab, you use an available ecommerce dataset to create a classification (logistic regression) model in BigQuery ML that predicts customers' purchasing habits.

**Focus on data engineering aspects:**
- Feature selection strategies
- Handling categorical features
- Creating training/test splits
- Data sampling techniques

**Feature selection in BigQuery:**
```sql
-- Check feature correlation
SELECT
  CORR(feature1, label) as corr_f1,
  CORR(feature2, label) as corr_f2
FROM dataset.training_data;

-- Get feature statistics
SELECT
  COUNT(*) as total,
  AVG(feature1) as avg_f1,
  STDDEV(feature1) as std_f1
FROM dataset.training_data;
```

---

### Lab 4: Engineer Data for Predictive Modeling - Challenge Lab

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Engineer Data for Predictive Modeling with BigQuery ML: Challenge Lab | 15 min | [Start Lab](https://www.skills.google/paths/17/course_templates/627/labs/612995) |

**Description**: This challenge lab tests your skills and knowledge from the labs in the Engineer Data for Predictive Modeling with BigQuery ML skill badge.

**Challenge objectives:**
- Build end-to-end data pipeline
- Apply data transformations
- Prepare features for ML
- Create BigQuery ML model

**Success criteria:**
- [ ] Data extracted from source correctly
- [ ] Transformations applied properly
- [ ] Data loaded into BigQuery
- [ ] Model trained successfully
- [ ] Predictions generated

---

## Data Engineering for ML Best Practices

### Data Quality Dimensions

| Dimension | Description | Check Method |
|-----------|-------------|--------------|
| Completeness | No missing critical values | NULL counts |
| Accuracy | Data reflects reality | Validation rules |
| Consistency | Same format across records | Type checks |
| Timeliness | Data is current | Timestamp analysis |
| Uniqueness | No unwanted duplicates | Key uniqueness |

### Feature Engineering Strategies

**Numerical Features:**
```sql
-- Normalization
(value - MIN(value) OVER()) / (MAX(value) OVER() - MIN(value) OVER())

-- Standardization
(value - AVG(value) OVER()) / STDDEV(value) OVER()

-- Log transformation
LOG(value + 1)

-- Binning
CASE
  WHEN value < 10 THEN 'low'
  WHEN value < 50 THEN 'medium'
  ELSE 'high'
END
```

**Date/Time Features:**
```sql
EXTRACT(YEAR FROM date) as year,
EXTRACT(MONTH FROM date) as month,
EXTRACT(DAYOFWEEK FROM date) as day_of_week,
EXTRACT(HOUR FROM timestamp) as hour,
DATE_DIFF(CURRENT_DATE(), date, DAY) as days_since
```

---

## End of Day Checklist

- [ ] Completed: Creating a Data Transformation Pipeline with Cloud Dataprep (45 min)
- [ ] Completed: ETL Processing with Dataflow and BigQuery (1 hr)
- [ ] Completed: Predict Visitor Purchases Classification (25 min)
- [ ] Completed: Challenge Lab (15 min)
- [ ] Understand feature engineering strategies
- [ ] Know data quality best practices

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 8 covers [Feature Engineering](https://www.skills.google/paths/17/course_templates/11) in depth, including Vertex AI Feature Store and TensorFlow Transform.
