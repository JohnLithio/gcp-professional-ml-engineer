# Day 4: December 31, 2025 - Prepare Data for ML APIs (Part 2)

## Overview
Today completes the data preparation labs with a focus on pre-trained ML APIs for language, speech, and video analysis.

## Exam Section Coverage
- **Section 1.2**: Building applications using ML APIs (Cloud Vision API, Natural Language API, Cloud Speech API)
- **Section 2.1**: Exploring and preprocessing organization-wide data

## Time Estimate: ~3 hours

---

## Course: Prepare Data for ML APIs on Google Cloud (Continued)

**Course Link**: [Prepare Data for ML APIs on Google Cloud](https://www.skills.google/paths/17/course_templates/631)

Complete the remaining labs today.

---

### Lab 5: Cloud Natural Language API: Qwik Start

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Cloud Natural Language API: Qwik Start | 10 min | [Start Lab](https://www.skills.google/paths/17/course_templates/631/labs/594533) |

**Description**: The Cloud Natural Language API lets you extract entities and perform sentiment and syntactic analysis on text.

**What you'll learn:**
- Analyze text sentiment
- Extract entities from text
- Classify content into categories
- Analyze syntax

**Key API capabilities:**
| Feature | Description |
|---------|-------------|
| Sentiment Analysis | Determine positive/negative sentiment |
| Entity Recognition | Identify people, places, events |
| Content Classification | Categorize text into topics |
| Syntax Analysis | Parse grammatical structure |

**Sample API call:**
```bash
curl "https://language.googleapis.com/v1/documents:analyzeSentiment" \
  -H "Authorization: Bearer $(gcloud auth print-access-token)" \
  -H "Content-Type: application/json" \
  -d '{
    "document": {
      "type": "PLAIN_TEXT",
      "content": "Google Cloud is amazing!"
    }
  }'
```

---

### Lab 6: Speech-to-Text API: Qwik Start

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Speech-to-Text API: Qwik Start | 10 min | [Start Lab](https://www.skills.google/paths/17/course_templates/631/labs/594534) |

**Description**: The Speech-to-Text API integrates speech recognition into dev apps; you can now send audio and receive a text transcription.

**What you'll learn:**
- Convert audio to text
- Handle different audio formats
- Work with synchronous and asynchronous recognition
- Configure recognition settings

**Key features:**
- Supports 125+ languages
- Real-time streaming recognition
- Automatic punctuation
- Speaker diarization (identify speakers)

**Sample request:**
```json
{
  "config": {
    "encoding": "LINEAR16",
    "sampleRateHertz": 16000,
    "languageCode": "en-US"
  },
  "audio": {
    "uri": "gs://bucket/audio.wav"
  }
}
```

---

### Lab 7: Video Intelligence: Qwik Start

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Video Intelligence: Qwik Start | 10 min | [Start Lab](https://www.skills.google/paths/17/course_templates/631/labs/594535) |

**Description**: In this lab, you use the Google Cloud Video Intelligence API to extract metadata from a sample video file.

**What you'll learn:**
- Detect labels in videos
- Track objects across frames
- Detect explicit content
- Recognize text in videos (OCR)

**Key features:**
| Feature | Description |
|---------|-------------|
| Label Detection | Identify objects, locations, activities |
| Shot Detection | Detect scene changes |
| Object Tracking | Track objects across frames |
| Text Detection | OCR for video content |
| Explicit Content | Safe search detection |

---

### Lab 8: Prepare Data for ML APIs - Challenge Lab

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Lab | Prepare Data for ML APIs on Google Cloud: Challenge Lab | 35 min | [Start Lab](https://www.skills.google/paths/17/course_templates/631/labs/594536) |

**Description**: This challenge lab tests your skills and knowledge from the labs in the Prepare Data for ML APIs on Google Cloud course. You should be familiar with the content of the labs before attempting this lab.

**What you'll demonstrate:**
- Combine skills from all previous labs
- Build an end-to-end data preparation pipeline
- Use multiple APIs together
- Handle real-world data scenarios

**Preparation tips:**
- Review all previous labs before starting
- Read challenge requirements carefully
- Plan your approach before executing
- Test incrementally

---

## Pre-trained APIs Summary

| API | Use Case | Input | Output |
|-----|----------|-------|--------|
| **Vision API** | Image analysis | Images | Labels, faces, text, objects |
| **Natural Language API** | Text analysis | Text | Sentiment, entities, syntax |
| **Speech-to-Text** | Audio transcription | Audio | Text transcription |
| **Text-to-Speech** | Voice synthesis | Text | Audio |
| **Video Intelligence** | Video analysis | Video | Labels, shots, objects |
| **Translation API** | Language translation | Text | Translated text |

---

## Key Terms to Know

| Term | Definition |
|------|------------|
| **Sentiment Analysis** | Determining emotional tone of text |
| **Entity Recognition** | Identifying named entities in text |
| **OCR** | Optical Character Recognition - extracting text from images |
| **Diarization** | Identifying different speakers in audio |
| **Shot Detection** | Identifying scene changes in video |

---

## End of Day Checklist

- [ ] Completed: Cloud Natural Language API: Qwik Start (10 min)
- [ ] Completed: Speech-to-Text API: Qwik Start (10 min)
- [ ] Completed: Video Intelligence: Qwik Start (10 min)
- [ ] Completed: Challenge Lab (35 min)
- [ ] Understand all pre-trained API capabilities
- [ ] Know when to use each API

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Happy New Year! Enjoy January 1st off. Day 5 (January 2nd) covers [Working with Notebooks in Vertex AI](https://www.skills.google/paths/17/course_templates/923) and begins [Create ML Models with BigQuery ML](https://www.skills.google/paths/17/course_templates/626).
