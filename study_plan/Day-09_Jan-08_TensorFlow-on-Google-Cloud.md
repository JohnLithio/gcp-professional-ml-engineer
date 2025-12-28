# Day 9: January 8, 2026 - TensorFlow on Google Cloud

## Overview
Today covers TensorFlow fundamentals, building neural networks with Keras, and training at scale on Vertex AI.

## Exam Section Coverage
- **Section 3.1**: Choosing ML framework and model architecture
- **Section 3.2**: Training models with different SDKs
- **Section 3.2**: Using distributed training for reliable pipelines
- **Section 3.3**: Evaluation of compute and accelerator options

## Time Estimate: ~6 hours

---

## Course: Build, Train and Deploy ML Models with Keras on Google Cloud

**Course Link**: [Build, Train and Deploy ML Models with Keras](https://www.skills.google/paths/17/course_templates/12)

---

### Module 1: Introduction to the TensorFlow Ecosystem

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Course introduction | 2 min | [Watch](https://www.skills.google/course_templates/12/video/582562) |
| Video | Introduction to the TensorFlow ecosystem | 5 min | [Watch](https://www.skills.google/course_templates/12/video/582563) |
| Video | Components of TensorFlow: Tensors and variables | 8 min | [Watch](https://www.skills.google/course_templates/12/video/582564) |
| Video | Getting started with the TensorFlow Keras API | 5 min | [Watch](https://www.skills.google/course_templates/12/video/582565) |
| Lab | TensorFlow: Getting Started with Keras | 2 hrs | [Start Lab](https://www.skills.google/course_templates/12/labs/582566) |
| Video | Summary | 1 min | [Watch](https://www.skills.google/course_templates/12/video/582567) |
| Quiz | The TensorFlow Ecosystem: Quiz | 35 min | [Take Quiz](https://www.skills.google/course_templates/12/quizzes/582568) |
| Reading | The TensorFlow Ecosystem: Resources | 30 min | [Read](https://www.skills.google/course_templates/12/documents/582569) |

---

### Module 2: Design and Build an Input Data Pipeline

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Introduction | 3 min | [Watch](https://www.skills.google/course_templates/12/video/582570) |
| Video | An ML recap | 9 min | [Watch](https://www.skills.google/course_templates/12/video/582571) |
| Video | Training on large datasets | 5 min | [Watch](https://www.skills.google/course_templates/12/video/582572) |
| Video | Lab introduction | 1 min | [Watch](https://www.skills.google/course_templates/12/video/582573) |
| Lab | Classifying Structured Data using Keras Preprocessing Layers | 1 hr | [Start Lab](https://www.skills.google/course_templates/12/labs/582574) |
| Video | Summary | 2 min | [Watch](https://www.skills.google/course_templates/12/video/582575) |
| Quiz | Design and Build a TensorFlow Input Data Pipeline: Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/12/quizzes/582576) |
| Reading | Design and Build a TensorFlow Input Data Pipeline: Resources | 30 min | [Read](https://www.skills.google/course_templates/12/documents/582577) |

**tf.data pipeline pattern:**
```python
dataset = tf.data.Dataset.list_files(file_pattern)
dataset = dataset.interleave(tf.data.TFRecordDataset, num_parallel_calls=tf.data.AUTOTUNE)
dataset = dataset.shuffle(buffer_size=10000)
dataset = dataset.map(parse_example, num_parallel_calls=tf.data.AUTOTUNE)
dataset = dataset.batch(batch_size)
dataset = dataset.prefetch(tf.data.AUTOTUNE)
```

---

### Module 3: Building Neural Networks with TensorFlow and Keras API

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Introduction | 3 min | [Watch](https://www.skills.google/course_templates/12/video/582578) |
| Video | Activation functions | 8 min | [Watch](https://www.skills.google/course_templates/12/video/582579) |
| Video | Neural Networks with Keras Sequential API | 5 min | [Watch](https://www.skills.google/course_templates/12/video/582580) |
| Video | Lab introduction | 1 min | [Watch](https://www.skills.google/course_templates/12/video/582581) |
| Lab | Building a DNN using the Keras Functional API | 1 hr | [Start Lab](https://www.skills.google/course_templates/12/labs/582582) |
| Video | Keras Functional API | 8 min | [Watch](https://www.skills.google/course_templates/12/video/582583) |
| Video | Model Subclassing | 2 min | [Watch](https://www.skills.google/course_templates/12/video/582584) |
| Video | Regularization basics | 6 min | [Watch](https://www.skills.google/course_templates/12/video/582585) |
| Video | Summary | 2 min | [Watch](https://www.skills.google/course_templates/12/video/582586) |
| Quiz | Building Neural Networks with the TensorFlow and Keras API: Quiz | 35 min | [Take Quiz](https://www.skills.google/course_templates/12/quizzes/582587) |
| Reading | Building Neural Networks with the TensorFlow and Keras API: Resources | 30 min | [Read](https://www.skills.google/course_templates/12/documents/582588) |

---

### Module 4: Training at Scale with Vertex AI

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Video | Introduction | 3 min | [Watch](https://www.skills.google/course_templates/12/video/582589) |
| Video | Training at scale | 7 min | [Watch](https://www.skills.google/course_templates/12/video/582590) |
| Video | Lab introduction | 1 min | [Watch](https://www.skills.google/course_templates/12/video/582591) |
| Lab | Vertex AI: Running Distributed TensorFlow Training on Vertex AI | 2 hrs | [Start Lab](https://www.skills.google/course_templates/12/labs/582592) |
| Video | Lab solution | 10 min | [Watch](https://www.skills.google/course_templates/12/video/582593) |
| Video | Course summary | 5 min | [Watch](https://www.skills.google/course_templates/12/video/582594) |
| Quiz | Training at Scale with Vertex AI: Quiz | 25 min | [Take Quiz](https://www.skills.google/course_templates/12/quizzes/582595) |
| Reading | Training at Scale with Vertex AI: Resources | 30 min | [Read](https://www.skills.google/course_templates/12/documents/582596) |
| Reading | Course Resources | 30 min | [Read](https://www.skills.google/course_templates/12/documents/582597) |

---

## Distributed Training Strategies

```python
# MirroredStrategy - Single machine, multiple GPUs
strategy = tf.distribute.MirroredStrategy()

# MultiWorkerMirroredStrategy - Multiple machines
strategy = tf.distribute.MultiWorkerMirroredStrategy()

# TPUStrategy - For TPU training
resolver = tf.distribute.cluster_resolver.TPUClusterResolver()
tf.config.experimental_connect_to_cluster(resolver)
tf.tpu.experimental.initialize_tpu_system(resolver)
strategy = tf.distribute.TPUStrategy(resolver)

# Use strategy
with strategy.scope():
    model = create_model()
    model.compile(optimizer='adam', loss='mse')
```

---

## End of Day Checklist

- [ ] Completed Module 1: TensorFlow Ecosystem (with lab)
- [ ] Completed Module 2: Input Data Pipelines (with lab)
- [ ] Completed Module 3: Neural Networks with Keras (with lab)
- [ ] Completed Module 4: Training at Scale (with lab)
- [ ] Understand distributed training strategies
- [ ] Know Vertex AI training job structure

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 10 covers [Production Machine Learning Systems](https://www.skills.google/paths/17/course_templates/17).
