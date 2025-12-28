# Day 17: January 20, 2026 - Review Sections 4-6 & Practice Questions

## Overview
Today provides a comprehensive review of exam Sections 4-6 and extensive practice with sample questions.

## Exam Section Coverage
- **Review**: Section 4 (Serving and Scaling Models)
- **Review**: Section 5 (Automating ML Pipelines)
- **Review**: Section 6 (Monitoring ML Solutions)

## Learning Objectives
- Review Sections 4-6 exam topics
- Practice sample questions
- Identify knowledge gaps
- Strengthen weak areas

---

## Course Links for Reference

| Resource | Link |
|----------|------|
| Production ML Systems | [Course Link](https://www.skills.google/paths/17/course_templates/17) |
| MLOps: Getting Started | [Course Link](https://www.skills.google/paths/17/course_templates/158) |
| MLOps with Vertex AI: Manage Features | [Course Link](https://www.skills.google/paths/17/course_templates/584) |
| MLOps for Generative AI | [Course Link](https://www.skills.google/paths/17/course_templates/927) |
| Sample Exam Questions | [Exam Page](https://cloud.google.com/learn/certification/machine-learning-engineer) |

---

## Section 4 Review: Serving and Scaling Models

### 4.1 Serving Models
**Key topics:**
- [ ] Batch vs online prediction
- [ ] Vertex AI endpoints
- [ ] Pre/post processing in serving
- [ ] Scaling for traffic

**Serving Comparison:**
| Aspect | Batch Prediction | Online Prediction |
|--------|------------------|-------------------|
| Latency | High (minutes-hours) | Low (milliseconds) |
| Use case | Large datasets | Real-time requests |
| Cost | Lower per prediction | Higher per prediction |
| Scaling | Job-based | Auto-scaling |

**Vertex AI Serving Options:**
```python
from google.cloud import aiplatform

# Deploy model to endpoint
endpoint = aiplatform.Endpoint.create(display_name='my-endpoint')

deployed_model = endpoint.deploy(
    model=model,
    deployed_model_display_name='my-deployed-model',
    machine_type='n1-standard-4',
    min_replica_count=1,
    max_replica_count=10,
    traffic_percentage=100
)

# Online prediction
prediction = endpoint.predict(instances=[{"feature1": value1}])

# Batch prediction
batch_job = model.batch_predict(
    job_display_name='my-batch-job',
    gcs_source='gs://bucket/input.jsonl',
    gcs_destination_prefix='gs://bucket/output/',
    machine_type='n1-standard-4'
)
```

### 4.2 Scaling for Performance
**Key topics:**
- [ ] Auto-scaling configuration
- [ ] GPU/TPU for serving
- [ ] Caching predictions
- [ ] Load balancing

**Scaling Decision Tree:**
```
Traffic Pattern?
├── Steady → Fixed replicas
├── Variable → Auto-scaling
└── Spiky → Pre-scaling + auto-scaling

Latency Requirements?
├── <10ms → Consider caching
├── <100ms → GPU serving
└── <1000ms → CPU serving (cost-effective)
```

---

## Section 5 Review: Automating ML Pipelines

### 5.1 Designing ML Pipelines
**Key topics:**
- [ ] Pipeline components
- [ ] Vertex AI Pipelines
- [ ] Kubeflow Pipelines
- [ ] TFX integration

**Pipeline Architecture:**
```
┌──────────────────────────────────────────────────────────────┐
│                    ML Pipeline Flow                           │
├──────────────────────────────────────────────────────────────┤
│                                                               │
│   Data       Feature        Training      Evaluation          │
│   Ingestion → Engineering → Job        → & Validation        │
│                                                               │
│                     │                          │              │
│                     ▼                          ▼              │
│              Model Registry            Deployment             │
│                     │                  (if passed)            │
│                     ▼                          │              │
│              Feature Store                     ▼              │
│                                         Monitoring            │
│                                                               │
└──────────────────────────────────────────────────────────────┘
```

**Vertex AI Pipeline Example:**
```python
from kfp.v2 import dsl
from kfp.v2.dsl import component
from google.cloud import aiplatform

@component
def preprocess_data(input_path: str, output_path: str):
    # Preprocessing logic
    pass

@component
def train_model(data_path: str, model_path: str):
    # Training logic
    pass

@dsl.pipeline(name='ml-pipeline')
def pipeline(input_data: str):
    preprocess_task = preprocess_data(input_path=input_data)
    train_task = train_model(data_path=preprocess_task.output)

# Compile and run
from kfp.v2 import compiler
compiler.Compiler().compile(pipeline, 'pipeline.json')

aiplatform.PipelineJob(
    display_name='my-pipeline',
    template_path='pipeline.json',
    parameter_values={'input_data': 'gs://bucket/data'}
).run()
```

### 5.2 CI/CD for ML
**Key topics:**
- [ ] Continuous training
- [ ] Model versioning
- [ ] Artifact management
- [ ] Testing strategies

**CI/CD Pipeline Stages:**
| Stage | Actions |
|-------|---------|
| Code | Unit tests, linting, code review |
| Data | Data validation, schema checks |
| Model | Training, evaluation, comparison |
| Deploy | Canary, shadow, A/B testing |
| Monitor | Performance tracking, alerts |

### 5.3 Hybrid/Multi-cloud
**Key topics:**
- [ ] Anthos for ML
- [ ] Edge deployment
- [ ] Data residency
- [ ] Portability strategies

---

## Section 6 Review: Monitoring ML Solutions

### 6.1 Identifying Risks
**Key topics:**
- [ ] Model degradation causes
- [ ] Data quality issues
- [ ] Security vulnerabilities
- [ ] Compliance risks

**Risk Categories:**
| Risk Type | Examples | Mitigation |
|-----------|----------|------------|
| Data | Drift, quality, bias | Monitoring, validation |
| Model | Degradation, staleness | Retraining, versioning |
| System | Latency, availability | Auto-scaling, redundancy |
| Security | Data leakage, attacks | Encryption, access control |

### 6.2 Monitoring and Troubleshooting
**Key topics:**
- [ ] Vertex AI Model Monitoring
- [ ] Training-serving skew detection
- [ ] Feature attribution drift
- [ ] Alert configuration

**Monitoring Setup:**
```python
from google.cloud import aiplatform

# Create monitoring job
monitoring_job = aiplatform.ModelDeploymentMonitoringJob.create(
    display_name='monitoring-job',
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
                        'feature1': {'value': 0.3}
                    }
                },
                'prediction_drift_detection_config': {
                    'drift_thresholds': {
                        'feature1': {'value': 0.3}
                    }
                }
            }
        }
    ],
    model_deployment_monitoring_schedule_config={
        'monitor_interval': {'seconds': 3600}
    },
    alert_config={
        'email_alert_config': {
            'user_emails': ['alert@example.com']
        }
    }
)
```

---

## Practice Questions - Sections 4-6

### Section 4: Serving and Scaling
1. When would you use batch prediction vs online prediction?
2. How do you configure auto-scaling for a Vertex AI endpoint?
3. What factors affect prediction latency?
4. How do you implement pre/post processing for serving?
5. When would you use GPUs for inference?

### Section 5: ML Pipelines
6. What are the components of a typical ML pipeline?
7. How do you implement continuous training?
8. What's the difference between Kubeflow Pipelines and TFX?
9. How do you handle model versioning in production?
10. What testing strategies apply to ML pipelines?

### Section 6: Monitoring
11. What causes training-serving skew and how do you detect it?
12. How do you set up feature attribution drift detection?
13. What metrics should you monitor for production ML models?
14. How do you configure alerts for model degradation?
15. What's the difference between data drift and concept drift?

---

## Practice Question Answers

### Section 4 Answers
1. **Batch vs Online**: Batch for large datasets processed periodically; online for real-time, low-latency needs
2. **Auto-scaling**: Set min/max replicas, target CPU utilization, scale-down delay
3. **Latency factors**: Model size, hardware, network, preprocessing complexity
4. **Pre/post processing**: Custom prediction containers or separate preprocessing services
5. **GPU inference**: Large models, parallel operations, high throughput needs

### Section 5 Answers
6. **Pipeline components**: Data ingestion, preprocessing, training, evaluation, deployment, monitoring
7. **Continuous training**: Scheduled triggers, data drift triggers, performance threshold triggers
8. **Kubeflow vs TFX**: Kubeflow is more flexible; TFX provides standardized components for TensorFlow
9. **Model versioning**: Model Registry, metadata tracking, semantic versioning
10. **Testing strategies**: Unit tests, integration tests, model validation, shadow testing

### Section 6 Answers
11. **Training-serving skew**: Different preprocessing or data distributions; detect with statistical tests
12. **Attribution drift**: Monitor SHAP/feature importance values over time, alert on changes
13. **Metrics to monitor**: Latency, throughput, error rates, prediction distributions, accuracy (if labels available)
14. **Alert configuration**: Set thresholds for drift metrics, configure email/PagerDuty notifications
15. **Data vs concept drift**: Data drift is input distribution change; concept drift is relationship change between features and target

---

## Key Comparisons Table

| Topic | Option A | Option B | When to Choose |
|-------|----------|----------|----------------|
| Prediction | Batch | Online | Latency requirements |
| Pipeline | Kubeflow | TFX | Framework flexibility vs TF integration |
| Monitoring | Sampling | Full | Cost vs completeness |
| Deployment | Blue-green | Canary | Speed vs risk reduction |
| Scaling | Vertical | Horizontal | Resource type vs volume |

---

## End of Day Checklist

- [ ] Reviewed Section 4: Serving and Scaling
- [ ] Reviewed Section 5: ML Pipelines
- [ ] Reviewed Section 6: Monitoring
- [ ] Completed practice questions
- [ ] Identified weak areas for tomorrow's review
- [ ] Reviewed code examples

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 18 (January 21st) is your final review day before the exam. Focus on:
- Comprehensive glossary review
- Sample exam questions
- Final knowledge gaps
- Exam logistics and strategies
