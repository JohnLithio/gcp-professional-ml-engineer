# Day 1: December 28, 2025 - Introduction to AI and Machine Learning on Google Cloud

## Overview
Today covers the foundations of AI/ML on Google Cloud, including AI infrastructure, BigQuery ML basics, and an introduction to Generative AI.

## Exam Section Coverage
- **Section 1.1**: Developing ML models using BigQuery ML
- **Section 1.2**: Choosing pre-trained ML APIs for business requirements
- **Section 3.1**: Choosing the appropriate ML framework and model architecture

## Time Estimate: ~4 hours

---

## Course: Introduction to AI and Machine Learning on Google Cloud

**Course Link**: [Introduction to AI and ML on Google Cloud](https://www.skills.google/paths/17/course_templates/593)

---

### Module 1: Introduction
| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Course introduction | 4 min | [Watch](https://www.skills.google/course_templates/593/video/598120) |

---

### Module 2: AI Foundations

**Learning Goals**: Understand AI use cases, Google Cloud AI infrastructure, and BigQuery ML basics.

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | A use case | 6 min | [Watch](https://www.skills.google/course_templates/593/video/598121) |
| Video | AI on Google Cloud | 5 min | [Watch](https://www.skills.google/course_templates/593/video/598122) |
| Video | AI infrastructure | 7 min | [Watch](https://www.skills.google/course_templates/593/video/598123) |
| Video | AI models | 6 min | [Watch](https://www.skills.google/course_templates/593/video/598124) |
| Video | BigQuery ML | 6 min | [Watch](https://www.skills.google/course_templates/593/video/598125) |
| Lab | Predict Visitor Purchases with BigQuery ML | 1 hr | [Start Lab](https://www.skills.google/course_templates/593/labs/598126) |
| Video | Summary | 3 min | [Watch](https://www.skills.google/course_templates/593/video/598127) |
| Quiz | AI Foundations Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/593/quizzes/598128) |
| Reading | AI Foundations Reading | 30 min | [Read](https://www.skills.google/course_templates/593/documents/598129) |

**Lab Description**: In this lab, you learn how to create and evaluate a machine learning model with BigQuery ML and use the model to predict purchase behavior.

---

### Module 3: Generative AI

**Learning Goals**: Understand foundation models, prompt engineering, and AI agents on Google Cloud.

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Generative AI on Google Cloud | 4 min | [Watch](https://www.skills.google/course_templates/593/video/598130) |
| Video | Foundation models | 8 min | [Watch](https://www.skills.google/course_templates/593/video/598131) |
| Video | Idea to app | 10 min | [Watch](https://www.skills.google/course_templates/593/video/598132) |
| Video | Prompt engineering | 8 min | [Watch](https://www.skills.google/course_templates/593/video/598133) |
| Video | Deployment and model tuning | 8 min | [Watch](https://www.skills.google/course_templates/593/video/598134) |
| Lab | Get Started with Vertex AI Studio | 1 hr | [Start Lab](https://www.skills.google/course_templates/593/labs/598135) |
| Video | AI agents | 7 min | [Watch](https://www.skills.google/course_templates/593/video/598136) |
| Video | Agent building with Google Cloud | 9 min | [Watch](https://www.skills.google/course_templates/593/video/598137) |
| Video | Summary | 4 min | [Watch](https://www.skills.google/course_templates/593/video/598138) |
| Quiz | Generative AI Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/593/quizzes/598139) |
| Reading | Generative AI Reading List | 30 min | [Read](https://www.skills.google/course_templates/593/documents/598140) |

**Lab Description**: In this lab, you learn to build generative AI prototypes with Vertex AI Studio and Gemini, mastering prompt design and multimodal analysis in the console, all without coding.

---

## Key Concepts to Master

### BigQuery ML
- **What it is**: ML directly in BigQuery using SQL
- **Key model types**: LINEAR_REG, LOGISTIC_REG, KMEANS, ARIMA_PLUS, BOOSTED_TREE_CLASSIFIER
- **Key functions**: CREATE MODEL, ML.EVALUATE, ML.PREDICT

```sql
-- Example: Create a classification model
CREATE OR REPLACE MODEL `dataset.model_name`
OPTIONS(model_type='logistic_reg') AS
SELECT
  feature1,
  feature2,
  label
FROM `dataset.training_table`;
```

### Google Cloud AI Infrastructure
| Component | Purpose |
|-----------|---------|
| Vertex AI | Unified ML platform |
| TPUs | Custom ML accelerators |
| GPUs | General-purpose accelerators |
| BigQuery ML | SQL-based ML |

### Generative AI Foundations
- **Foundation Models**: Large pre-trained models (Gemini, PaLM)
- **Prompt Engineering**: Designing effective prompts for LLMs
- **Fine-tuning**: Adapting models to specific tasks
- **AI Agents**: Autonomous systems that can take actions

---

## End of Day Checklist

### Module 1: Introduction
- [ ] Watched: Course introduction (4 min)

### Module 2: AI Foundations
- [ ] Watched: A use case (6 min)
- [ ] Watched: AI on Google Cloud (5 min)
- [ ] Watched: AI infrastructure (7 min)
- [ ] Watched: AI models (6 min)
- [ ] Watched: BigQuery ML (6 min)
- [ ] Completed: Predict Visitor Purchases with BigQuery ML lab (1 hr)
- [ ] Watched: Summary (3 min)
- [ ] Passed: AI Foundations Quiz
- [ ] Read: AI Foundations Reading

### Module 3: Generative AI
- [ ] Watched: Generative AI on Google Cloud (4 min)
- [ ] Watched: Foundation models (8 min)
- [ ] Watched: Idea to app (10 min)
- [ ] Watched: Prompt engineering (8 min)
- [ ] Watched: Deployment and model tuning (8 min)
- [ ] Completed: Get Started with Vertex AI Studio lab (1 hr)
- [ ] Watched: AI agents (7 min)
- [ ] Watched: Agent building with Google Cloud (9 min)
- [ ] Watched: Summary (4 min)
- [ ] Passed: Generative AI Quiz
- [ ] Read: Generative AI Reading List

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 2 continues with the remaining modules of this course: AI Development Options and the ML Workflow, plus deeper dives into pre-trained APIs and AutoML.
