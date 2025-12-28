# Day 13: January 14, 2026 - Building Generative AI Applications

## Overview
Today covers building practical Generative AI applications on Google Cloud, including RAG applications, prompt engineering, and using Vertex AI.

## Exam Section Coverage
- **Section 1.2**: Implementing RAG applications with Vertex AI Agent Builder
- **Section 1.2**: Building applications by using foundational models
- **Section 3.2**: Fine-tuning foundational models

## Time Estimate: ~6 hours

---

## Course: Create Generative AI Apps on Google Cloud

**Course Link**: [Create Generative AI Apps on Google Cloud](https://www.skills.google/paths/17/course_templates/1120)

---

### Module 1: Generative AI Applications

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Reading | Getting started | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532034) |
| Reading | Introduction to generative AI applications | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532035) |
| Reading | Foundation models | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532036) |
| Reading | Challenges of Gen AI for applications | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532037) |
| Reading | Summary | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532038) |
| Quiz | Generative AI Applications Quiz | 40 min | [Take Quiz](https://www.skills.google/course_templates/1120/quizzes/532039) |

**GenAI Application Types:**
| Type | Description | Example |
|------|-------------|---------|
| Text Generation | Generate new text content | Content writing |
| Summarization | Condense long text | Document summaries |
| Q&A | Answer questions from context | Customer support |
| Code Generation | Generate code | Developer assistance |
| Conversational | Multi-turn dialogue | Chatbots |

---

### Module 2: Prompts

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Reading | Getting started | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532040) |
| Reading | Introduction to prompts | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532041) |
| Reading | Prompt structure | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532042) |
| Reading | Prompt engineering | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532043) |
| Reading | Summary | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532044) |
| Quiz | Prompts Quiz | 40 min | [Take Quiz](https://www.skills.google/course_templates/1120/quizzes/532045) |
| Lab | Get Started with Vertex AI Studio | 1 hr | [Start Lab](https://www.skills.google/course_templates/1120/labs/532046) |

**Lab Description**: In this lab, you learn to build generative AI prototypes with Vertex AI Studio and Gemini, mastering prompt design and multimodal analysis in the console, all without coding.

**Prompt Engineering Techniques:**
```python
# Zero-shot prompting
prompt_zero_shot = """
Classify the sentiment of this review as positive, negative, or neutral:
Review: "The product exceeded my expectations!"
Sentiment:
"""

# Few-shot prompting
prompt_few_shot = """
Classify the sentiment:

Review: "Great product!" -> Sentiment: positive
Review: "Terrible experience" -> Sentiment: negative
Review: "It's okay" -> Sentiment: neutral
Review: "The product exceeded my expectations!" -> Sentiment:
"""

# Chain-of-thought prompting
prompt_cot = """
Solve this step by step:
Question: If John has 5 apples and gives away 2, then buys 3 more, how many?

Let me think through this:
1. John starts with 5 apples
2. He gives away 2: 5 - 2 = 3 apples
3. He buys 3 more: 3 + 3 = 6 apples

Answer: John has 6 apples.
"""
```

---

### Module 3: Retrieval Augmented Generation (RAG)

| Type | Activity | Duration | Link |
|------|----------|----------|------|
| Reading | Getting started | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532047) |
| Reading | Improving foundation model accuracy | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532048) |
| Reading | Retrieval Augmented Generation (RAG) | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532049) |
| Reading | Retrieving relevant data | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532050) |
| Reading | RAG architecture using Vertex AI | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532051) |
| Reading | Summary | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532052) |
| Quiz | Retrieval Augmented Generation Quiz | 40 min | [Take Quiz](https://www.skills.google/course_templates/1120/quizzes/532053) |
| Lab | Build an LLM and RAG-based Chat Application with AlloyDB and Vertex AI | 2 hrs | [Start Lab](https://www.skills.google/course_templates/1120/labs/532054) |
| Reading | Course resources | 30 min | [Read](https://www.skills.google/course_templates/1120/documents/532055) |

**Lab Description**: In this lab, you create a chat application that uses Retrieval Augmented Generation, or RAG, to augment prompts with data retrieved from AlloyDB.

**RAG Architecture:**
```
┌──────────────────────────────────────────────────────────────┐
│                     RAG Pipeline                              │
├──────────────────────────────────────────────────────────────┤
│                                                               │
│   Document Processing:                                        │
│   ┌──────────┐   ┌──────────┐   ┌──────────┐                │
│   │Documents │──►│ Chunking │──►│Embeddings│──►Vector DB     │
│   └──────────┘   └──────────┘   └──────────┘                │
│                                                               │
│   Query Processing:                                           │
│   ┌─────────┐   ┌──────────┐   ┌─────────┐   ┌──────────┐   │
│   │  Query  │──►│ Embedding│──►│ Search  │──►│ Context  │   │
│   └─────────┘   └──────────┘   └─────────┘   └────┬─────┘   │
│                                                    │          │
│   Response Generation:                             ▼          │
│   ┌─────────────────────────────────────────────────────┐   │
│   │  Prompt = Query + Retrieved Context + Instructions   │   │
│   └───────────────────────┬─────────────────────────────┘   │
│                           │                                  │
│                    ┌──────▼──────┐                          │
│                    │    LLM      │                          │
│                    │  (Gemini)   │                          │
│                    └──────┬──────┘                          │
│                           │                                  │
│                    ┌──────▼──────┐                          │
│                    │  Response   │                          │
│                    └─────────────┘                          │
└──────────────────────────────────────────────────────────────┘
```

**RAG Implementation with Vertex AI:**
```python
from vertexai.preview import rag
from vertexai.generative_models import GenerativeModel

# Create RAG corpus
corpus = rag.create_corpus(display_name="my_rag_corpus")

# Import documents
rag.import_files(
    corpus_name=corpus.name,
    paths=["gs://bucket/documents/"],
    chunk_size=500,
    chunk_overlap=50
)

# Query with RAG
model = GenerativeModel("gemini-1.5-pro")
response = rag.retrieval_query(
    rag_resources=[corpus.name],
    text="What is the return policy?",
    similarity_top_k=5
)

# Generate response with context
prompt = f"Context: {response.contexts}\n\nQuestion: What is the return policy?"
result = model.generate_content(prompt)
```

---

## Key Terms to Know

| Term | Definition |
|------|------------|
| **RAG** | Retrieval Augmented Generation - enhancing LLM with external knowledge |
| **Embedding** | Dense vector representation of text |
| **Chunking** | Splitting documents into smaller pieces |
| **Vector Database** | Database optimized for similarity search |
| **Grounding** | Connecting LLM responses to factual sources |
| **Zero-shot** | Prompting without examples |
| **Few-shot** | Prompting with examples |

---

## End of Day Checklist

### Module 1: Generative AI Applications
- [ ] Read: Getting started
- [ ] Read: Introduction to generative AI applications
- [ ] Read: Foundation models
- [ ] Read: Challenges of Gen AI for applications
- [ ] Read: Summary
- [ ] Passed: Generative AI Applications Quiz

### Module 2: Prompts
- [ ] Read: Getting started
- [ ] Read: Introduction to prompts
- [ ] Read: Prompt structure
- [ ] Read: Prompt engineering
- [ ] Read: Summary
- [ ] Passed: Prompts Quiz
- [ ] Completed: Get Started with Vertex AI Studio lab (1 hr)

### Module 3: Retrieval Augmented Generation
- [ ] Read: All 6 RAG readings
- [ ] Passed: Retrieval Augmented Generation Quiz
- [ ] Completed: Build LLM and RAG-based Chat Application lab (2 hrs)
- [ ] Read: Course resources

---

## Notes Section
*Use this space for your own notes during study:*




---

## Tomorrow's Preview
Day 14 covers ML Pipelines and Orchestration, including Vertex AI Pipelines, TFX, Kubeflow Pipelines, and CI/CD for ML.
