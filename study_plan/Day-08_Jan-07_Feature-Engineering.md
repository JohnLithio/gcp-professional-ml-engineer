# Day 8: January 7, 2026 - Feature Engineering

## Overview
Today provides a comprehensive deep-dive into feature engineering, Vertex AI Feature Store, and TensorFlow Transform.

## Exam Section Coverage
- **Section 2.1**: Creating and consolidating features in Vertex AI Feature Store
- **Section 4.2**: Vertex AI Feature Store for serving
- **Section 5.1**: Ensuring consistent data preprocessing between training and serving

## Time Estimate: ~5 hours

---

## Course: Feature Engineering

**Course Link**: [Feature Engineering](https://www.skills.google/paths/17/course_templates/11)

---

### Module 1: Introduction to Vertex AI Feature Store

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Course introduction | 1 min | [Watch](https://www.skills.google/course_templates/11/video/582631) |
| Video | Benefits of Feature Store | 4 min | [Watch](https://www.skills.google/course_templates/11/video/582632) |
| Video | Feature store terminology | 5 min | [Watch](https://www.skills.google/course_templates/11/video/582633) |
| Video | Vertex AI Feature Store | 6 min | [Watch](https://www.skills.google/course_templates/11/video/582634) |
| Quiz | Introduction to Vertex AI Feature Store: Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/11/quizzes/582635) |

---

### Module 2: Raw Data to Features

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Introduction | <1 min | [Watch](https://www.skills.google/course_templates/11/video/582636) |
| Video | Goodness of a feature | 3 min | [Watch](https://www.skills.google/course_templates/11/video/582637) |
| Video | Numeric features | 2 min | [Watch](https://www.skills.google/course_templates/11/video/582638) |
| Video | Categorical features | 4 min | [Watch](https://www.skills.google/course_templates/11/video/582639) |
| Video | Feature crosses | 4 min | [Watch](https://www.skills.google/course_templates/11/video/582640) |
| Video | Summary | 1 min | [Watch](https://www.skills.google/course_templates/11/video/582641) |
| Quiz | Raw Data to Features: Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/11/quizzes/582642) |
| Reading | Raw Data to Features: Resources | 30 min | [Read](https://www.skills.google/course_templates/11/documents/582643) |

---

### Module 3: Feature Engineering

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Introduction | 3 min | [Watch](https://www.skills.google/course_templates/11/video/582644) |
| Video | Compare legacy Feature Engineering | 6 min | [Watch](https://www.skills.google/course_templates/11/video/582645) |
| Video | Apache Beam and Dataflow | 3 min | [Watch](https://www.skills.google/course_templates/11/video/582646) |
| Video | Dataflow: streaming and batch processing | 5 min | [Watch](https://www.skills.google/course_templates/11/video/582647) |
| Video | Lab introduction | 1 min | [Watch](https://www.skills.google/course_templates/11/video/582648) |
| Lab | Performing Basic Feature Engineering in BQML | 1 hr | [Start Lab](https://www.skills.google/course_templates/11/labs/582649) |
| Video | Lab solution | 15 min | [Watch](https://www.skills.google/course_templates/11/video/582650) |
| Quiz | Feature Engineering: Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/11/quizzes/582651) |
| Reading | Feature Engineering: Resources | 30 min | [Read](https://www.skills.google/course_templates/11/documents/582652) |

---

### Module 4: Preprocessing and Feature Creation

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Introduction | 3 min | [Watch](https://www.skills.google/course_templates/11/video/582653) |
| Video | Data preprocessing best practices | 4 min | [Watch](https://www.skills.google/course_templates/11/video/582654) |
| Video | Preprocessing at scale | 6 min | [Watch](https://www.skills.google/course_templates/11/video/582655) |
| Video | Summary | <1 min | [Watch](https://www.skills.google/course_templates/11/video/582656) |
| Quiz | Preprocessing and Feature Creation: Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/11/quizzes/582657) |
| Reading | Preprocessing and Feature Creation: Resources | 30 min | [Read](https://www.skills.google/course_templates/11/documents/582658) |

---

### Module 5: Feature Crosses - TensorFlow Playground

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Feature crosses introduction | 4 min | [Watch](https://www.skills.google/course_templates/11/video/582659) |
| Video | Incorporating feature crosses | 1 min | [Watch](https://www.skills.google/course_templates/11/video/582660) |
| Video | Sparsity and regularization | 4 min | [Watch](https://www.skills.google/course_templates/11/video/582661) |
| Video | Summary | 1 min | [Watch](https://www.skills.google/course_templates/11/video/582662) |
| Lab | Performing Advanced Feature Engineering in BQML | 1 hr | [Start Lab](https://www.skills.google/course_templates/11/labs/582663) |
| Quiz | Feature Crosses: Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/11/quizzes/582664) |
| Reading | Feature Crosses: Resources | 30 min | [Read](https://www.skills.google/course_templates/11/documents/582665) |

**TensorFlow Playground exercise:** Go to [playground.tensorflow.org](https://playground.tensorflow.org/) and experiment with feature crosses (X1*X2).

---

### Module 6: Introduction to TensorFlow Transform

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Introduction | 3 min | [Watch](https://www.skills.google/course_templates/11/video/582666) |
| Video | tf.Transform | 6 min | [Watch](https://www.skills.google/course_templates/11/video/582667) |
| Video | Analyzers | 5 min | [Watch](https://www.skills.google/course_templates/11/video/582668) |
| Video | Summary | 2 min | [Watch](https://www.skills.google/course_templates/11/video/582669) |
| Quiz | TensorFlow Transform: Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/11/quizzes/582670) |
| Reading | TensorFlow Transform: Resources | 30 min | [Read](https://www.skills.google/course_templates/11/documents/582671) |
| Reading | Course Resources | 30 min | [Read](https://www.skills.google/course_templates/11/documents/582672) |

**TensorFlow Transform example:**
```python
import tensorflow_transform as tft

def preprocessing_fn(inputs):
    outputs = {}
    outputs['scaled_feature'] = tft.scale_to_z_score(inputs['raw_feature'])
    outputs['bucketized'] = tft.bucketize(inputs['continuous'], num_buckets=5)
    outputs['category_id'] = tft.compute_and_apply_vocabulary(inputs['category'])
    return outputs
```

---

## End of Day Checklist

- [ ] Completed Module 1: Introduction to Vertex AI Feature Store
- [ ] Completed Module 2: Raw Data to Features
- [ ] Completed Module 3: Feature Engineering (with lab)
- [ ] Completed Module 4: Preprocessing and Feature Creation
- [ ] Completed Module 5: Feature Crosses (with lab)
- [ ] Completed Module 6: TensorFlow Transform
- [ ] Practiced with TensorFlow Playground

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 9 covers [Build, Train and Deploy ML Models with Keras on Google Cloud](https://www.skills.google/paths/17/course_templates/12).
