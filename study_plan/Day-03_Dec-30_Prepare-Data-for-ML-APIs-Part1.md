# Day 3: December 30, 2025 - Prepare Data for ML APIs (Part 1)

## Overview
Today focuses on hands-on labs covering data processing tools essential for ML workflows: Dataprep, Dataflow, and the Cloud Vision API.

## Exam Section Coverage
- **Section 1.2**: Building AI solutions by using ML APIs
- **Section 2.1**: Exploring and preprocessing organization-wide data

## Time Estimate: ~3 hours

---

## Course: Prepare Data for ML APIs on Google Cloud

**Course Link**: [Prepare Data for ML APIs on Google Cloud](https://www.skills.google/paths/17/course_templates/631)

This is a hands-on lab course. Complete the first 4 labs today.

---

### Lab 1: Dataprep: Qwik Start

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Dataprep: Qwik Start | 20 min | [Start Lab](https://www.skills.google/paths/17/course_templates/631/labs/594528) |

**Description**: Google Cloud Dataprep is an intelligent data service for visually exploring, cleaning, and preparing data for analysis.

**What you'll learn:**
- Use Cloud Dataprep for data preparation
- Clean and transform data visually
- Handle missing values and outliers
- Export transformed data

**Key skills:**
- [ ] Data wrangling with Dataprep
- [ ] Visual data transformation
- [ ] Data quality assessment

**Important concepts:**
- Dataprep is a no-code data preparation tool
- Useful for exploring and cleaning raw data
- Integrates with BigQuery and Cloud Storage

---

### Lab 2: Dataflow: Qwik Start - Templates

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Dataflow: Qwik Start - Templates | 15 min | [Start Lab](https://www.skills.google/paths/17/course_templates/631/labs/594529) |

**Description**: In this lab, you learn how to create a streaming pipeline using a Google-provided Dataflow template.

**What you'll learn:**
- Use Dataflow templates for common data processing tasks
- Run batch and streaming pipelines
- Monitor pipeline execution

**Key skills:**
- [ ] Deploying Dataflow templates
- [ ] Understanding pipeline parameters
- [ ] Monitoring job execution

**Important concepts:**
- Dataflow is fully managed for batch and streaming data processing
- Templates provide pre-built solutions for common patterns
- Based on Apache Beam

---

### Lab 3: Dataflow: Qwik Start - Python

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Dataflow: Qwik Start - Python | 20 min | [Start Lab](https://www.skills.google/paths/17/course_templates/631/labs/594530) |

**Description**: In this lab, you set up your Python development environment for Dataflow (using the Apache Beam SDK for Python) and run an example Dataflow pipeline.

**What you'll learn:**
- Write custom Dataflow pipelines in Python
- Use Apache Beam SDK
- Process data with transforms
- Write to BigQuery

**Key skills:**
- [ ] Apache Beam pipeline structure
- [ ] Common transforms (ParDo, GroupByKey)
- [ ] Pipeline I/O connectors

**Code pattern to understand:**
```python
import apache_beam as beam

with beam.Pipeline() as pipeline:
    (pipeline
     | 'Read' >> beam.io.ReadFromText('input.txt')
     | 'Transform' >> beam.Map(process_function)
     | 'Write' >> beam.io.WriteToBigQuery('table'))
```

---

### Lab 4: Cloud Vision API: Qwik Start

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Google Cloud Vision API | 20 min | [Start Lab](https://www.skills.google/paths/17/course_templates/631/labs/594531) |

**Description**: Use the Vision API to detect faces, labels, landmarks, and text in images.

**What you'll learn:**
- Detect labels in images
- Identify faces and landmarks
- Extract text from images (OCR)
- Detect explicit content

**Key API capabilities:**
| Feature | Description |
|---------|-------------|
| Label Detection | Identify objects, locations, activities |
| Face Detection | Detect faces and expressions |
| Landmark Detection | Identify famous landmarks |
| Text Detection (OCR) | Extract text from images |
| Safe Search | Detect explicit content |

**Key skills:**
- [ ] Making Vision API requests
- [ ] Interpreting API responses
- [ ] Understanding confidence scores

---

## Data Processing Comparison

| Tool | Use Case | Processing Type |
|------|----------|-----------------|
| **Dataprep** | Interactive data exploration & cleaning | Batch |
| **Dataflow** | Scalable data pipelines | Batch & Streaming |
| **Dataproc** | Spark/Hadoop workloads | Batch |
| **BigQuery** | SQL-based analytics | Batch & Streaming |

---

## Key Terms to Know

| Term | Definition |
|------|------------|
| **ETL** | Extract, Transform, Load - data processing pattern |
| **Apache Beam** | Unified programming model for batch and streaming |
| **Dataflow** | Fully managed service for Apache Beam pipelines |
| **Dataprep** | Visual data preparation tool |
| **Vision API** | Pre-trained API for image analysis |

---

## End of Day Checklist

- [ ] Completed: Dataprep: Qwik Start (20 min)
- [ ] Completed: Dataflow: Qwik Start - Templates (15 min)
- [ ] Completed: Dataflow: Qwik Start - Python (20 min)
- [ ] Completed: Cloud Vision API (20 min)
- [ ] Understand when to use each data processing tool
- [ ] Familiar with Apache Beam pipeline structure

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 4 continues with ML APIs labs including Natural Language API, Speech-to-Text, Video Intelligence, and the Challenge Lab within the [Prepare Data for ML APIs](https://www.skills.google/paths/17/course_templates/631) course.
