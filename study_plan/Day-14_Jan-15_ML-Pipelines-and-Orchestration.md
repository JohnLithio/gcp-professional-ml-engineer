# Day 14: January 15, 2026 - ML Pipelines and Orchestration

## Overview
Today covers ML pipeline development and orchestration, including Vertex AI Pipelines, TFX, and Kubeflow.

## Exam Section Coverage
- **Section 5.1**: Developing end-to-end ML pipelines
- **Section 5.1**: Orchestration framework (Kubeflow Pipelines, Vertex AI Pipelines, Cloud Composer)
- **Section 5.1**: System design with TFX components or Kubeflow DSL
- **Section 5.2**: CI/CD model deployment

## Learning Objectives
- Build ML pipelines with Vertex AI Pipelines
- Understand TFX pipeline components
- Learn Kubeflow Pipelines basics
- Implement CI/CD for ML

---

## Course Links

| Resource | Link |
|----------|------|
| Production ML Systems (Pipeline content) | [Course Link](https://www.skills.google/paths/17/course_templates/17) |
| ML Engineer Learning Path | [Full Path](https://www.skills.google/paths/17) |
| Vertex AI Pipelines Documentation | [Documentation](https://cloud.google.com/vertex-ai/docs/pipelines) |

---

## Study Materials

### Vertex AI Pipelines

**What it is:**
- Serverless ML pipeline orchestration
- Based on Kubeflow Pipelines
- Integrated with Vertex AI services

**Pipeline Architecture:**
```
┌────────────────────────────────────────────────────────────────┐
│                    Vertex AI Pipeline                           │
├────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐   │
│   │   Data   │──►│  Train   │──►│ Evaluate │──►│  Deploy  │   │
│   │  Ingest  │   │  Model   │   │  Model   │   │  Model   │   │
│   └──────────┘   └──────────┘   └──────────┘   └──────────┘   │
│        │              │              │              │          │
│        └──────────────┴──────────────┴──────────────┘          │
│                              │                                  │
│                    ┌─────────▼──────────┐                      │
│                    │    ML Metadata     │                      │
│                    │  (Artifact Store)  │                      │
│                    └────────────────────┘                      │
└────────────────────────────────────────────────────────────────┘
```

**Building a Pipeline:**
```python
from kfp import dsl
from kfp.dsl import component
from google.cloud import aiplatform

# Define a component
@component(base_image='python:3.9')
def preprocess_data(
    input_data: str,
    output_data: dsl.Output[dsl.Dataset]
):
    import pandas as pd
    df = pd.read_csv(input_data)
    # Preprocessing logic
    df.to_csv(output_data.path, index=False)

@component(base_image='python:3.9')
def train_model(
    training_data: dsl.Input[dsl.Dataset],
    model: dsl.Output[dsl.Model]
):
    import pandas as pd
    from sklearn.ensemble import RandomForestClassifier
    import joblib

    df = pd.read_csv(training_data.path)
    X, y = df.drop('target', axis=1), df['target']
    clf = RandomForestClassifier()
    clf.fit(X, y)
    joblib.dump(clf, model.path)

# Define the pipeline
@dsl.pipeline(name='training-pipeline')
def training_pipeline(input_data: str):
    preprocess_task = preprocess_data(input_data=input_data)
    train_task = train_model(training_data=preprocess_task.outputs['output_data'])

# Compile and run
from kfp import compiler
compiler.Compiler().compile(training_pipeline, 'pipeline.json')

aiplatform.init(project='project-id', location='us-central1')
job = aiplatform.PipelineJob(
    display_name='my-pipeline',
    template_path='pipeline.json',
    parameter_values={'input_data': 'gs://bucket/data.csv'}
)
job.submit()
```

---

### TensorFlow Extended (TFX)

**TFX Components:**
| Component | Purpose |
|-----------|---------|
| ExampleGen | Data ingestion |
| StatisticsGen | Data statistics |
| SchemaGen | Schema inference |
| ExampleValidator | Data validation |
| Transform | Feature engineering |
| Trainer | Model training |
| Tuner | Hyperparameter tuning |
| Evaluator | Model evaluation |
| InfraValidator | Serving validation |
| Pusher | Model deployment |

**TFX Pipeline Example:**
```python
import tfx
from tfx.components import (
    CsvExampleGen, StatisticsGen, SchemaGen,
    ExampleValidator, Transform, Trainer, Evaluator, Pusher
)
from tfx.orchestration.experimental.interactive.interactive_context import InteractiveContext

# Create components
example_gen = CsvExampleGen(input_base='data/')
statistics_gen = StatisticsGen(examples=example_gen.outputs['examples'])
schema_gen = SchemaGen(statistics=statistics_gen.outputs['statistics'])
example_validator = ExampleValidator(
    statistics=statistics_gen.outputs['statistics'],
    schema=schema_gen.outputs['schema']
)
transform = Transform(
    examples=example_gen.outputs['examples'],
    schema=schema_gen.outputs['schema'],
    module_file='preprocessing.py'
)
trainer = Trainer(
    module_file='model.py',
    examples=transform.outputs['transformed_examples'],
    transform_graph=transform.outputs['transform_graph'],
    schema=schema_gen.outputs['schema']
)
```

---

### Kubeflow Pipelines

**Key Concepts:**
- Pipeline: DAG of components
- Component: Containerized step
- Experiment: Collection of runs
- Run: Single pipeline execution

**Component Types:**
```python
# Lightweight Python component
@dsl.component
def add(a: int, b: int) -> int:
    return a + b

# Container component
@dsl.container_component
def train_container():
    return dsl.ContainerSpec(
        image='gcr.io/project/train:latest',
        command=['python', 'train.py']
    )
```

---

### CI/CD for ML Pipelines

**ML CI/CD Pipeline:**
```
┌─────────────────────────────────────────────────────────────────┐
│                    CI/CD Pipeline                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│   Code Change                                                    │
│       │                                                          │
│       ▼                                                          │
│   ┌───────────────┐                                             │
│   │ Cloud Build   │                                             │
│   │ - Unit tests  │                                             │
│   │ - Lint        │                                             │
│   │ - Build image │                                             │
│   └───────┬───────┘                                             │
│           │                                                      │
│           ▼                                                      │
│   ┌───────────────┐                                             │
│   │   Artifact    │                                             │
│   │   Registry    │                                             │
│   └───────┬───────┘                                             │
│           │                                                      │
│           ▼                                                      │
│   ┌───────────────────────┐                                     │
│   │  Vertex AI Pipeline   │                                     │
│   │  - Training           │                                     │
│   │  - Evaluation         │                                     │
│   │  - Conditional deploy │                                     │
│   └───────────────────────┘                                     │
└─────────────────────────────────────────────────────────────────┘
```

**Cloud Build Configuration:**
```yaml
# cloudbuild.yaml
steps:
  # Run tests
  - name: 'python:3.9'
    entrypoint: 'pip'
    args: ['install', '-r', 'requirements.txt']

  - name: 'python:3.9'
    entrypoint: 'pytest'
    args: ['tests/']

  # Build and push container
  - name: 'gcr.io/cloud-builders/docker'
    args: ['build', '-t', 'gcr.io/$PROJECT_ID/trainer:$SHORT_SHA', '.']

  - name: 'gcr.io/cloud-builders/docker'
    args: ['push', 'gcr.io/$PROJECT_ID/trainer:$SHORT_SHA']

  # Trigger pipeline
  - name: 'python:3.9'
    entrypoint: 'python'
    args: ['run_pipeline.py', '--image-tag', '$SHORT_SHA']
```

---

## Orchestration Comparison

| Feature | Vertex AI Pipelines | Cloud Composer | Kubeflow Pipelines |
|---------|---------------------|----------------|-------------------|
| Based on | Kubeflow | Apache Airflow | Argo Workflows |
| Managed | Serverless | Managed | Self-managed |
| Best for | ML workflows | General DAGs | ML workflows |
| ML Integration | Native | Via operators | Native |

---

## Key Terms to Know

| Term | Definition |
|------|------------|
| **Pipeline** | DAG of ML operations |
| **Component** | Single step in a pipeline |
| **Artifact** | Output from a pipeline step |
| **ML Metadata** | Tracking of pipeline artifacts |
| **Orchestration** | Scheduling and managing pipelines |
| **CI/CD** | Continuous Integration/Continuous Deployment |

---

## Practice Questions

1. When would you use Vertex AI Pipelines vs Cloud Composer?
2. What are the key TFX components and their purposes?
3. How do you implement model validation in a pipeline?
4. What triggers should you use for continuous training?
5. How do you handle failed pipeline runs?

---

## End of Day Checklist

- [ ] Understand Vertex AI Pipelines architecture
- [ ] Know TFX components and their roles
- [ ] Can build simple KFP components
- [ ] Understand CI/CD patterns for ML
- [ ] Know when to use different orchestration tools

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 15 covers Responsible AI with [Fairness & Bias](https://www.skills.google/paths/17/course_templates/985), [Interpretability & Transparency](https://www.skills.google/paths/17/course_templates/989), and [Privacy & Safety](https://www.skills.google/paths/17/course_templates/1036).
