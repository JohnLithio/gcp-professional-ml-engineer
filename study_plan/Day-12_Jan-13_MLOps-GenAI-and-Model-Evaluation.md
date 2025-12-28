# Day 12: January 13, 2026 - MLOps for Generative AI and Model Evaluation

## Overview
Today covers MLOps practices specific to Generative AI and comprehensive model evaluation techniques for both traditional ML and GenAI.

## Exam Section Coverage
- **Section 2.3**: Evaluating generative AI solutions
- **Section 6.2**: Establishing continuous evaluation metrics
- **Section 3.2**: Fine-tuning foundational models

## Time Estimate: ~4 hours

---

## Course 1: Machine Learning Operations (MLOps) for Generative AI

**Course Link**: [MLOps for Generative AI](https://www.skills.google/paths/17/course_templates/927)

---

### Module: MLOps for GenAI

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Course Introduction | 1 min | [Watch](https://www.skills.google/course_templates/927/video/559263) |
| Video | The evolution of MLOps | 4 min | [Watch](https://www.skills.google/course_templates/927/video/559264) |
| Video | MLOps framework for Generative AI | 3 min | [Watch](https://www.skills.google/course_templates/927/video/559265) |
| Video | Navigating Generative AI: Embracing Nuances and Adapting MLOps | 12 min | [Watch](https://www.skills.google/course_templates/927/video/559266) |
| Video | Summary | 1 min | [Watch](https://www.skills.google/course_templates/927/video/559267) |

**GenAI MLOps Considerations:**
| Aspect | Traditional ML | Generative AI |
|--------|---------------|---------------|
| Training | Custom datasets | Fine-tuning on base models |
| Evaluation | Standard metrics | Human + automatic evaluation |
| Deployment | Model files | API endpoints + prompts |
| Versioning | Model weights | Model + prompt versions |
| Monitoring | Drift detection | Quality + safety monitoring |

**Fine-tuning Approaches:**
```
1. Full Fine-tuning
   - Update all model parameters
   - Requires significant compute
   - Best for domain adaptation

2. Parameter-Efficient Fine-tuning (PEFT)
   - Update subset of parameters
   - Lower compute requirements
   - LoRA, Adapter methods

3. Prompt Tuning
   - Train soft prompts
   - Model weights frozen
   - Very efficient
```

---

## Course 2: MLOps with Vertex AI: Model Evaluation

**Course Link**: [MLOps with Vertex AI: Model Evaluation](https://www.skills.google/paths/17/course_templates/1080)

---

### Module 1: Introduction to Model Evaluation

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Welcome to the course | 1 min | [Watch](https://www.skills.google/course_templates/1080/video/520167) |
| Video | Introduction to Model Evaluation | 8 min | [Watch](https://www.skills.google/course_templates/1080/video/520168) |
| Video | Model Evaluation within MLOps | 3 min | [Watch](https://www.skills.google/course_templates/1080/video/520169) |
| Video | Model Evaluation Challenges and Solutions offered by Vertex AI | 8 min | [Watch](https://www.skills.google/course_templates/1080/video/520170) |
| Quiz | MLOps: Introduction to Model Evaluation Quiz | 20 min | [Take Quiz](https://www.skills.google/course_templates/1080/quizzes/520171) |
| Reading | Reading List | 30 min | [Read](https://www.skills.google/course_templates/1080/documents/520172) |

**Classification Metrics:**
| Metric | Formula | Use Case |
|--------|---------|----------|
| Accuracy | (TP+TN)/(TP+TN+FP+FN) | Balanced classes |
| Precision | TP/(TP+FP) | Minimize false positives |
| Recall | TP/(TP+FN) | Minimize false negatives |
| F1-Score | 2*(P*R)/(P+R) | Balance precision/recall |
| AUC-ROC | Area under ROC | Overall performance |

**Regression Metrics:**
| Metric | Description |
|--------|-------------|
| MAE | Mean Absolute Error |
| MSE | Mean Squared Error |
| RMSE | Root Mean Squared Error |
| R² | Coefficient of determination |
| MAPE | Mean Absolute Percentage Error |

---

### Module 2: Model Evaluation for Generative AI

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Challenges of evaluating the generative AI tasks - Introduction | 4 min | [Watch](https://www.skills.google/course_templates/1080/video/520173) |
| Video | The Art and Science of Evaluating Large Language Models | 5 min | [Watch](https://www.skills.google/course_templates/1080/video/520174) |
| Video | Beyond Accuracy: Mastering Evaluation Metrics for Generative AI | 9 min | [Watch](https://www.skills.google/course_templates/1080/video/520175) |
| Video | Best Practices for LLM Evaluation | 5 min | [Watch](https://www.skills.google/course_templates/1080/video/520176) |
| Video | Solving Evaluation Challenges | 9 min | [Watch](https://www.skills.google/course_templates/1080/video/520177) |
| Video | Streamlining Model Evaluation with Computation-based Metrics | 3 min | [Watch](https://www.skills.google/course_templates/1080/video/520178) |
| Video | Comparing performance with Model based evaluation | 8 min | [Watch](https://www.skills.google/course_templates/1080/video/520179) |
| Quiz | MLOps: Model Evaluation for Generative AI Quiz | 35 min | [Take Quiz](https://www.skills.google/course_templates/1080/quizzes/520180) |
| Reading | Reading List | 30 min | [Read](https://www.skills.google/course_templates/1080/documents/520181) |
| Video | Course Summary | 2 min | [Watch](https://www.skills.google/course_templates/1080/video/520182) |

**Common GenAI Metrics:**
| Metric | Measures | Use Case |
|--------|----------|----------|
| BLEU | N-gram overlap | Translation |
| ROUGE | Recall-oriented overlap | Summarization |
| Perplexity | Model confidence | Language modeling |
| Coherence | Logical flow | Text generation |
| Groundedness | Factual accuracy | RAG applications |

---

## Key Terms to Know

| Term | Definition |
|------|------------|
| **BLEU Score** | Evaluates machine translation quality |
| **ROUGE Score** | Evaluates text summarization |
| **Perplexity** | Measures how well a model predicts text |
| **Groundedness** | Whether output is based on provided context |
| **Arbiter Model** | LLM used to evaluate other LLM outputs |
| **Human Evaluation** | Manual assessment of model outputs |

---

## End of Day Checklist

### MLOps for Generative AI
- [ ] Watched: Course Introduction
- [ ] Watched: The evolution of MLOps
- [ ] Watched: MLOps framework for Generative AI
- [ ] Watched: Navigating Generative AI: Embracing Nuances and Adapting MLOps
- [ ] Watched: Summary

### Model Evaluation - Module 1
- [ ] Watched: All Module 1 videos (4 videos)
- [ ] Passed: Introduction to Model Evaluation Quiz
- [ ] Read: Module 1 Reading List

### Model Evaluation - Module 2
- [ ] Watched: All Module 2 videos (8 videos)
- [ ] Passed: Model Evaluation for Generative AI Quiz
- [ ] Read: Module 2 Reading List

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 13 covers [Create Generative AI Apps on Google Cloud](https://www.skills.google/paths/17/course_templates/1120), including building RAG applications and prompt engineering.
