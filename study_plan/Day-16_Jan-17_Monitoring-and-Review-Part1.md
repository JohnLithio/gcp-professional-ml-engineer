# Day 16: January 17, 2026 - Monitoring ML Solutions & Review (Sections 1-3)

## Overview
Today covers monitoring ML solutions and provides a comprehensive review of exam Sections 1-3.

## Exam Section Coverage
- **Section 6.1**: Identifying risks to ML solutions
- **Section 6.2**: Monitoring, testing, and troubleshooting ML solutions
- **Review**: Sections 1-3 (Low-code ML, Data/Model Management, Scaling Prototypes)

## Learning Objectives
- Implement ML monitoring strategies
- Detect and handle model drift
- Review Sections 1-3 exam topics
- Practice sample questions

---

## Course Links

| Resource | Link |
|----------|------|
| Production ML Systems | [Course Link](https://www.skills.google/paths/17/course_templates/17) |
| Sample Exam Questions | [Exam Page](https://cloud.google.com/learn/certification/machine-learning-engineer) |
| Study Guide PDF | Review your downloaded study guide |

---

## Monitoring ML Solutions

### Training-Serving Skew

**What it is:**
Discrepancy between how data is processed during training vs serving.

**Types:**
| Type | Cause | Detection |
|------|-------|-----------|
| Data Skew | Different data distributions | Statistical tests |
| Feature Skew | Different feature engineering | Feature comparison |
| Schema Skew | Different data schemas | Schema validation |

**Detection:**
```python
from google.cloud import aiplatform

# Set up model monitoring
aiplatform.ModelDeploymentMonitoringJob.create(
    display_name='my-monitoring-job',
    endpoint=endpoint,
    logging_sampling_strategy={
        'random_sample_config': {'sample_rate': 0.8}
    },
    model_deployment_monitoring_objective_configs=[
        {
            'objective_config': {
                'training_dataset': training_dataset,
                'training_prediction_skew_detection_config': {
                    'skew_thresholds': {
                        'feature1': {'value': 0.3},
                        'feature2': {'value': 0.3}
                    }
                }
            }
        }
    ],
    model_deployment_monitoring_schedule_config={
        'monitor_interval': {'seconds': 3600}
    }
)
```

### Feature Attribution Drift

**What it is:**
Change in feature importance over time.

**Detection:**
- Compare feature attribution distributions
- Monitor SHAP/attribution values
- Alert on significant changes

### Model Performance Monitoring

**Metrics to track:**
- Prediction latency
- Throughput
- Error rates
- Resource utilization
- Model accuracy (if labels available)

**Monitoring Stack:**
```
┌────────────────────────────────────────────────────────────────┐
│                 Monitoring Architecture                         │
├────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ┌──────────────┐                                             │
│   │   Endpoint   │──► Prediction Logs ──► BigQuery             │
│   └──────────────┘         │                                   │
│                            │                                    │
│                   ┌────────▼────────┐                          │
│                   │ Vertex AI Model │                          │
│                   │   Monitoring    │                          │
│                   └────────┬────────┘                          │
│                            │                                    │
│           ┌────────────────┼────────────────┐                  │
│           ▼                ▼                ▼                  │
│   ┌───────────────┐ ┌───────────┐ ┌────────────────┐          │
│   │ Cloud         │ │ Alert     │ │ Dashboards     │          │
│   │ Monitoring    │ │ Policies  │ │ (Looker/BQ)    │          │
│   └───────────────┘ └───────────┘ └────────────────┘          │
└────────────────────────────────────────────────────────────────┘
```

---

## Section 1 Review: Architecting Low-Code ML Solutions

### 1.1 BigQuery ML
**Key topics:**
- [ ] Model types: linear_reg, logistic_reg, kmeans, arima_plus, boosted_tree
- [ ] CREATE MODEL syntax
- [ ] ML.EVALUATE, ML.PREDICT, ML.FORECAST functions
- [ ] Feature engineering in BQML (TRANSFORM clause)

**Quick reference:**
```sql
-- Classification
CREATE MODEL dataset.model OPTIONS(model_type='logistic_reg') AS SELECT...

-- Regression
CREATE MODEL dataset.model OPTIONS(model_type='linear_reg') AS SELECT...

-- Time series
CREATE MODEL dataset.model OPTIONS(model_type='arima_plus', time_series_timestamp_col='date') AS SELECT...

-- Clustering
CREATE MODEL dataset.model OPTIONS(model_type='kmeans', num_clusters=3) AS SELECT...
```

### 1.2 ML APIs and Foundational Models
**Key topics:**
- [ ] Pre-trained APIs: Vision, Natural Language, Speech, Video Intelligence
- [ ] Model Garden and Model types
- [ ] RAG applications with Vertex AI Agent Builder
- [ ] When to use pre-trained vs custom models

### 1.3 AutoML
**Key topics:**
- [ ] Data preparation for AutoML
- [ ] Supported data types: tabular, image, text, video
- [ ] AutoML training options
- [ ] Model debugging and configuration

---

## Section 2 Review: Collaborating Within and Across Teams

### 2.1 Data Exploration and Preprocessing
**Key topics:**
- [ ] Data storage options: Cloud Storage, BigQuery, Spanner, Cloud SQL
- [ ] Preprocessing tools: Dataflow, Dataprep, TFX
- [ ] Vertex AI Feature Store
- [ ] Privacy: PII handling, de-identification

### 2.2 Model Prototyping with Notebooks
**Key topics:**
- [ ] Vertex AI Workbench vs Colab Enterprise
- [ ] Security best practices
- [ ] Git integration
- [ ] Framework support: TensorFlow, PyTorch, Scikit-learn

### 2.3 Tracking and Running Experiments
**Key topics:**
- [ ] Vertex AI Experiments
- [ ] Vertex AI TensorBoard
- [ ] Evaluating generative AI solutions
- [ ] Experiment comparison

---

## Section 3 Review: Scaling Prototypes into ML Models

### 3.1 Building Models
**Key topics:**
- [ ] Framework selection (TensorFlow, PyTorch, JAX)
- [ ] Model architecture considerations
- [ ] Interpretability requirements
- [ ] Model complexity trade-offs

### 3.2 Training Models
**Key topics:**
- [ ] Custom training on Vertex AI
- [ ] Distributed training strategies
- [ ] Hyperparameter tuning
- [ ] Fine-tuning foundational models

### 3.3 Hardware Selection
**Key topics:**
- [ ] CPU vs GPU vs TPU
- [ ] When to use each
- [ ] Cost considerations
- [ ] Distributed training with GPUs/TPUs

**Hardware Selection Guide:**
| Use Case | Recommended |
|----------|-------------|
| Small models, inference | CPU |
| DNN training, parallel ops | GPU |
| Large TF models | TPU |
| Edge/mobile | Edge TPU, TF Lite |

---

## Practice Questions - Sections 1-3

### Section 1: Low-Code ML
1. Which BigQuery ML model type would you use for customer churn prediction?
2. When should you use pre-trained APIs vs custom models?
3. How do you evaluate an AutoML model's performance?

### Section 2: Data and Model Management
4. What's the purpose of Vertex AI Feature Store?
5. When would you choose Dataflow over Dataproc?
6. How do you handle PII in ML training data?

### Section 3: Scaling Prototypes
7. When would you choose TPU over GPU for training?
8. What distributed training strategy would you use for multi-GPU training on one machine?
9. How do you implement hyperparameter tuning in Vertex AI?

---

## Key Formulas and Metrics

**Classification:**
- Accuracy = (TP + TN) / (TP + TN + FP + FN)
- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN)
- F1 = 2 * (Precision * Recall) / (Precision + Recall)

**Regression:**
- MSE = (1/n) * Σ(y - ŷ)²
- RMSE = √MSE
- MAE = (1/n) * Σ|y - ŷ|
- R² = 1 - (SS_res / SS_tot)

---

## End of Day Checklist

- [ ] Understand monitoring strategies
- [ ] Reviewed Section 1: Low-Code ML
- [ ] Reviewed Section 2: Data/Model Management
- [ ] Reviewed Section 3: Scaling Prototypes
- [ ] Completed practice questions

---

## Week 3 Summary

**Courses completed this week:**
- MLOps for Generative AI
- Model Evaluation
- Create Generative AI Apps
- ML Pipelines and Orchestration
- Responsible AI (all three courses)
- Monitoring review

**Key skills:**
- GenAI MLOps
- Model evaluation
- RAG applications
- ML pipelines
- Responsible AI practices

---

## Notes Section
*Use this space for your own notes during study:*




---

## Weekend Break
Enjoy January 18-19 off! Day 17 (January 20th) covers review of Sections 4-6 and practice questions.
