# Day 15: January 16, 2026 - Responsible AI for Developers

## Overview
Today covers all three Responsible AI courses: Fairness & Bias, Interpretability & Transparency, and Privacy & Safety.

## Exam Section Coverage
- **Section 6.1**: Aligning with Google's Responsible AI practices
- **Section 6.1**: Assessing ML solution readiness (data bias, fairness)
- **Section 6.1**: Model explainability on Vertex AI
- **Section 2.1**: Privacy implications of data usage

## Time Estimate: ~8 hours

---

## Course 1: Responsible AI for Developers - Fairness & Bias

**Course Link**: [Responsible AI: Fairness & Bias](https://www.skills.google/paths/17/course_templates/985)

---

### Module 1: AI Responsibility Foundations

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Course Introduction | 1 min | [Watch](https://www.skills.google/course_templates/985/video/583527) |
| Video | AI & Responsibility | 6 min | [Watch](https://www.skills.google/course_templates/985/video/583528) |
| Video | Google's AI Principles | 5 min | [Watch](https://www.skills.google/course_templates/985/video/583529) |
| Video | Responsible AI Practices | 8 min | [Watch](https://www.skills.google/course_templates/985/video/583530) |
| Video | Case study: Google Flights | 6 min | [Watch](https://www.skills.google/course_templates/985/video/583531) |
| Quiz | Quiz | 20 min | [Take Quiz](https://www.skills.google/course_templates/985/quizzes/583532) |

---

### Module 2: Fairness and Bias

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Overview of Fairness and Bias | 8 min | [Watch](https://www.skills.google/course_templates/985/video/583533) |
| Video | Identify Bias - TFDV Tool | 5 min | [Watch](https://www.skills.google/course_templates/985/video/583534) |
| Video | Identify Bias - What-if Tool | 4 min | [Watch](https://www.skills.google/course_templates/985/video/583535) |
| Video | Identify Bias - TFMA Tool | 2 min | [Watch](https://www.skills.google/course_templates/985/video/583536) |
| Video | Mitigate Bias - Data Intervention | 7 min | [Watch](https://www.skills.google/course_templates/985/video/583537) |
| Video | Mitigate Bias - Threshold Calibration | 5 min | [Watch](https://www.skills.google/course_templates/985/video/583538) |
| Video | Mitigate Bias - Model Remediation | 5 min | [Watch](https://www.skills.google/course_templates/985/video/583539) |
| Video | Lab: Mitigate Bias with MinDiff in TensorFlow | 1 min | [Watch](https://www.skills.google/course_templates/985/video/583540) |
| Lab | Mitigate Bias with MinDiff in TensorFlow | 2 hrs | [Start Lab](https://www.skills.google/course_templates/985/labs/583541) |
| Quiz | Quiz | 15 min | [Take Quiz](https://www.skills.google/course_templates/985/quizzes/583542) |
| Video | Course Summary | 2 min | [Watch](https://www.skills.google/course_templates/985/video/583543) |
| Reading | Reading | 30 min | [Read](https://www.skills.google/course_templates/985/documents/583544) |
| Reading | Course Resources | 30 min | [Read](https://www.skills.google/course_templates/985/documents/583545) |

**Lab Description**: This lab helps you learn how to mitigate bias using MinDiff technique by leveraging TensorFlow Model Remediation library.

**Types of Bias:**
| Bias Type | Description | Example |
|-----------|-------------|---------|
| Historical | Past discrimination in data | Hiring data reflecting past bias |
| Sampling | Non-representative data | Training only on certain demographics |
| Measurement | Inconsistent data collection | Different evaluation criteria |
| Algorithmic | Model amplifies bias | Feedback loops |

**Mitigation Strategies:**
| Stage | Technique |
|-------|-----------|
| Pre-processing | Resampling, reweighting data |
| In-processing | Fairness constraints in training |
| Post-processing | Adjusting predictions |

---

## Course 2: Responsible AI - Interpretability & Transparency

**Course Link**: [Responsible AI: Interpretability & Transparency](https://www.skills.google/paths/17/course_templates/989)

---

### Module: Interpretability and Transparency

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Course Introduction | 1 min | [Watch](https://www.skills.google/course_templates/989/video/583392) |
| Video | Overview of interpretability and transparency | 4 min | [Watch](https://www.skills.google/course_templates/989/video/583393) |
| Video | Overview of interpretability techniques | 7 min | [Watch](https://www.skills.google/course_templates/989/video/583394) |
| Video | Feature based explanations: Model agnostic | 11 min | [Watch](https://www.skills.google/course_templates/989/video/583395) |
| Video | Feature based explanations: Model specific | 7 min | [Watch](https://www.skills.google/course_templates/989/video/583396) |
| Video | Concept-based and example-based explanations | 5 min | [Watch](https://www.skills.google/course_templates/989/video/583397) |
| Video | Tools for interpretability | 5 min | [Watch](https://www.skills.google/course_templates/989/video/583398) |
| Video | Data and Model Transparency | 6 min | [Watch](https://www.skills.google/course_templates/989/video/583399) |
| Video | Lab: Vertex Explainable AI | 1 min | [Watch](https://www.skills.google/course_templates/989/video/583400) |
| Lab | Explaining an Image Classification Model with Vertex Explainable AI | 2 hrs | [Start Lab](https://www.skills.google/course_templates/989/labs/583401) |
| Quiz | Quiz | 15 min | [Take Quiz](https://www.skills.google/course_templates/989/quizzes/583402) |
| Video | Course Summary | 2 min | [Watch](https://www.skills.google/course_templates/989/video/583403) |
| Reading | Reading | 30 min | [Read](https://www.skills.google/course_templates/989/documents/583404) |
| Reading | Course Resources | 30 min | [Read](https://www.skills.google/course_templates/989/documents/583405) |

**Lab Description**: In this lab, you learn how to deploy an explainable image model with Vertex AI.

**Interpretability Methods:**
| Method | Type | Description |
|--------|------|-------------|
| SHAP | Model-agnostic | Feature contribution scores |
| LIME | Model-agnostic | Local linear approximations |
| Integrated Gradients | Model-specific (DNN) | Attribution based on gradients |
| Attention weights | Model-specific | What the model focuses on |
| Feature importance | Model-specific | Tree-based importance |

**Vertex AI Explainable AI:**
```python
from google.cloud import aiplatform

# Create model with explanations enabled
model = aiplatform.Model.upload(
    display_name='my-model',
    artifact_uri='gs://bucket/model/',
    serving_container_image_uri='...',
    explanation_metadata={
        'inputs': {'features': {}},
        'outputs': {'predictions': {}}
    },
    explanation_parameters={
        'sampled_shapley_attribution': {
            'path_count': 10
        }
    }
)

# Get explanations with predictions
endpoint = model.deploy()
response = endpoint.explain(instances=[instance])
print(response.explanations)
```

---

## Course 3: Responsible AI - Privacy & Safety

**Course Link**: [Responsible AI: Privacy & Safety](https://www.skills.google/paths/17/course_templates/1036)

---

### Module 1: AI Privacy

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Course Introduction | 1 min | [Watch](https://www.skills.google/course_templates/1036/video/584563) |
| Video | Overview of AI Privacy | 3 min | [Watch](https://www.skills.google/course_templates/1036/video/584564) |
| Video | Privacy in Training Data: De-identification techniques | 8 min | [Watch](https://www.skills.google/course_templates/1036/video/584565) |
| Video | Privacy in Training Data: Randomization techniques | 6 min | [Watch](https://www.skills.google/course_templates/1036/video/584566) |
| Video | Privacy in Machine Learning Training: DP-SGD | 3 min | [Watch](https://www.skills.google/course_templates/1036/video/584567) |
| Video | Privacy in Machine Learning Training: Federated Learning | 7 min | [Watch](https://www.skills.google/course_templates/1036/video/584568) |
| Video | System Security on Google Cloud | 4 min | [Watch](https://www.skills.google/course_templates/1036/video/584569) |
| Video | System Security on Gen AI | 4 min | [Watch](https://www.skills.google/course_templates/1036/video/584570) |
| Video | Lab: Differential Privacy in Machine Learning with TensorFlow Privacy | 1 min | [Watch](https://www.skills.google/course_templates/1036/video/584571) |
| Lab | Differential Privacy in Machine Learning with TensorFlow Privacy | 2 hrs | [Start Lab](https://www.skills.google/course_templates/1036/labs/584572) |
| Quiz | Module 1: Quiz | 15 min | [Take Quiz](https://www.skills.google/course_templates/1036/quizzes/584573) |

**Lab Description**: In this lab, you learn how to use differential privacy in machine learning using TensorFlow Privacy.

**De-identification Techniques:**
| Technique | Description | Reversible |
|-----------|-------------|------------|
| Redaction | Delete sensitive data | No |
| Masking | Replace with placeholder | No |
| Tokenization | Replace with token | Yes |
| Bucketing | Replace with range | No |
| Perturbation | Add noise | No |

---

### Module 2: AI Safety

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Overview of AI Safety | 5 min | [Watch](https://www.skills.google/course_templates/1036/video/584574) |
| Video | Safety Evaluation | 7 min | [Watch](https://www.skills.google/course_templates/1036/video/584575) |
| Video | Harms Prevention | 8 min | [Watch](https://www.skills.google/course_templates/1036/video/584576) |
| Video | Model Training for Safety: Instruction Fine-tuning | 4 min | [Watch](https://www.skills.google/course_templates/1036/video/584577) |
| Video | Model Training for Safety: RLHF | 3 min | [Watch](https://www.skills.google/course_templates/1036/video/584578) |
| Video | Safety in Google Cloud GenAI | 7 min | [Watch](https://www.skills.google/course_templates/1036/video/584579) |
| Video | Lab: Safeguarding with Vertex AI Gemini API | <1 min | [Watch](https://www.skills.google/course_templates/1036/video/584580) |
| Lab | Safeguarding with Vertex AI Gemini API | 2 hrs | [Start Lab](https://www.skills.google/course_templates/1036/labs/584581) |
| Quiz | Module 2: Quiz | 15 min | [Take Quiz](https://www.skills.google/course_templates/1036/quizzes/584582) |
| Video | Course Summary | 2 min | [Watch](https://www.skills.google/course_templates/1036/video/584583) |
| Reading | Reading | 30 min | [Read](https://www.skills.google/course_templates/1036/documents/584584) |
| Reading | Course Resources | 30 min | [Read](https://www.skills.google/course_templates/1036/documents/584585) |

**Lab Description**: In this lab, you learn how to inspect the safety ratings returned from the Vertex AI Gemini API and how to set a safety threshold to filter responses.

**Safety for LLMs:**
```python
# Safety settings for Gemini
from vertexai.generative_models import GenerativeModel, HarmCategory, HarmBlockThreshold

model = GenerativeModel('gemini-1.5-pro')

safety_settings = {
    HarmCategory.HARM_CATEGORY_HATE_SPEECH: HarmBlockThreshold.BLOCK_MEDIUM_AND_ABOVE,
    HarmCategory.HARM_CATEGORY_DANGEROUS_CONTENT: HarmBlockThreshold.BLOCK_MEDIUM_AND_ABOVE,
    HarmCategory.HARM_CATEGORY_SEXUALLY_EXPLICIT: HarmBlockThreshold.BLOCK_MEDIUM_AND_ABOVE,
    HarmCategory.HARM_CATEGORY_HARASSMENT: HarmBlockThreshold.BLOCK_MEDIUM_AND_ABOVE,
}

response = model.generate_content(
    prompt,
    safety_settings=safety_settings
)
```

---

## Google's AI Principles

1. Be socially beneficial
2. Avoid creating or reinforcing unfair bias
3. Be built and tested for safety
4. Be accountable to people
5. Incorporate privacy design principles
6. Uphold high standards of scientific excellence
7. Be made available for uses that accord with these principles

---

## Key Terms to Know

| Term | Definition |
|------|------------|
| **Fairness** | Equitable treatment across groups |
| **Bias** | Systematic error in predictions |
| **Interpretability** | Understanding model decisions |
| **Explainability** | Ability to explain predictions |
| **Differential Privacy** | Mathematical framework for privacy |
| **De-identification** | Removing identifying information |
| **Model Card** | Documentation of model characteristics |
| **Adversarial Robustness** | Resistance to malicious inputs |

---

## End of Day Checklist

### Fairness & Bias
- [ ] Watched: Module 1 videos (5 videos)
- [ ] Passed: Module 1 Quiz
- [ ] Watched: Module 2 videos (8 videos)
- [ ] Completed: Mitigate Bias with MinDiff lab (2 hrs)
- [ ] Passed: Module 2 Quiz
- [ ] Read: Reading and Course Resources

### Interpretability & Transparency
- [ ] Watched: All videos (10 videos)
- [ ] Completed: Explaining Image Classification Model lab (2 hrs)
- [ ] Passed: Quiz
- [ ] Read: Reading and Course Resources

### Privacy & Safety
- [ ] Watched: Module 1 videos (9 videos)
- [ ] Completed: Differential Privacy lab (2 hrs)
- [ ] Passed: Module 1 Quiz
- [ ] Watched: Module 2 videos (7 videos)
- [ ] Completed: Safeguarding with Vertex AI Gemini API lab (2 hrs)
- [ ] Passed: Module 2 Quiz
- [ ] Read: Reading and Course Resources

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 16 covers Monitoring ML Solutions and a comprehensive review of Exam Sections 1-3.
