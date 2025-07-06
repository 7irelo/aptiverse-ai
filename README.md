# 🧠 Aptiverse AI Models – FastAPI Microservice for AI-Powered Learning and Student Support

The **Aptiverse AI Models** service powers the intelligence layer of the Aptiverse platform. It is a **modular FastAPI application** built with cutting-edge **Python ML and NLP libraries**, serving as the reasoning engine for understanding students’ goals, emotions, behaviors, academic struggles, and strengths.

This microservice is designed to be **asynchronous, secure, and extensible**—connected to the main `.NET 8 Aptiverse API` through a **RabbitMQ-based message queue**, with fallback support for direct REST requests.

---

## 🧠 What It Does

The AI engine provides emotional, psychological, and academic insight, acting like a personalized tutor, counselor, and career coach for students.

### 📝 Diary & Emotion Analysis

* Analyzes free-form student journaling.
* Identifies emotion, trauma, burnout, anxiety, motivation.
* Responds empathetically like a psychologist using NLP.

### 🧮 Math Image Reasoning

* Accepts uploaded photos of handwritten math working.
* Extracts math steps and patterns.
* Analyzes cognitive approach to problem-solving.
* Identifies careless errors vs conceptual misunderstandings.

### 🎯 Goal Feasibility & Career Planning

* Students input goals (e.g., “study medicine at UCT”).
* Models check academic history vs university requirements.
* Advises on realistic steps, timeframes, and progress.
* Recommends alternate options when needed.

### 📊 Academic Reports & Recommendations

* Models collaborate like a neural reasoning graph.
* Produce teacher/parent reports (with privacy protections).
* Suggest academic interventions based on risk and performance.

### 🧪 Auto-Generated Tests

* Generates personalized practice tests from past SA exam papers.
* Custom difficulty and topic targeting.

### 🏅 Reward System Engine

* Students are rewarded with premium features for consistency and goal achievement.

---

## 🛠️ Tech Stack

| Layer            | Technology                                                                                |
| ---------------- | ----------------------------------------------------------------------------------------- |
| API Framework    | FastAPI (Python)                                                                          |
| ML/NLP Libraries | `scikit-learn`, `transformers`, `pandas`, `matplotlib`, `cv2`, `torch`, `spaCy`, `Pillow` |
| Model Serving    | Custom PyTorch/Sklearn models, HuggingFace pipelines                                      |
| Image Analysis   | OpenCV + custom handwriting segmentation                                                  |
| Emotion Models   | DistilBERT fine-tuned for emotion/mental health                                           |
| Data Sources     | PostgreSQL, CSV (admissions data), OCR                                                    |
| Message Queue    | RabbitMQ (via Aptiverse Worker)                                                           |
| DevOps           | Uvicorn, Docker, GitHub Actions                                                           |

---

## 📁 Project Structure

```bash
aptiverse-ai/
├── app/
│   ├── main.py                      # FastAPI entry point
│   ├── api/                         # Route handlers
│   │   ├── diary.py                 # /diary endpoint
│   │   ├── math_image.py           # /math-image endpoint
│   │   ├── goals.py                # /goals endpoint
│   │   ├── report.py               # /report endpoint
│   │   └── reward.py               # /reward endpoint
│   ├── models/                     # Core AI/ML logic
│   │   ├── diary_model.py          # Emotion/Trauma NLP model
│   │   ├── math_model.py           # Image-based math reasoning
│   │   ├── goal_model.py           # Goal feasibility logic
│   │   ├── test_gen_model.py       # Test generation engine
│   │   ├── recommender.py          # Strength/weakness analysis
│   │   └── orchestrator.py         # Coordinates cross-model logic
│   ├── schemas/                    # Pydantic data contracts
│   │   ├── diary.py
│   │   ├── goals.py
│   │   └── report.py
│   ├── data/
│   │   ├── db.py                   # SQLAlchemy engine & session
│   │   ├── models.py              # SQLAlchemy table definitions (e.g., University)
│   │   └── universities.py        # University data loader (from DB)
│   ├── ml_artifacts/               # Pretrained/fine-tuned models
│   ├── services/
│   │   └── utils.py                # Shared helpers
│   └── config.py                   # Environment + DB config
├── tests/
│   ├── test_diary.py
│   └── test_math.py
├── requirements.txt
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone & Set Up Environment

```bash
git clone https://github.com/your-org/aptiverse-ai.git
cd aptiverse-ai
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 2. Start Local Dev Server

```bash
uvicorn app.main:app --reload
```

Access the docs:
👉 `http://localhost:8000/docs`

---

## 🔌 Integration Channels

This AI service can be accessed by:

* ✅ **Aptiverse Worker** (.NET 8 service via RabbitMQ)
* 🔁 Optional fallback: direct `HTTP POST` from Aptiverse API
* 🧠 Internal model orchestrator via Python function calls

---

## 🔍 API Examples

| Endpoint            | Method | Description                           |
| ------------------- | ------ | ------------------------------------- |
| `/diary/analyze`    | POST   | Emotion + NLP response generation     |
| `/math-image/solve` | POST   | Extracts + reasons about math steps   |
| `/goals/evaluate`   | POST   | Goal feasibility vs real-world data   |
| `/report/generate`  | POST   | Student performance & risk report     |
| `/test/generate`    | POST   | Personalized academic test generation |

---

## 🧠 Example Use Case

**Input:**

```json
{
  "text": "I feel overwhelmed by my math work. I keep trying but always fail."
}
```

**Output:**

```json
{
  "emotions": [
    { "label": "frustrated", "score": 0.91 },
    { "label": "sad", "score": 0.76 }
  ],
  "response": "It’s okay to feel this way. You’re not alone. Let’s look at what’s causing the frustration and how we can break it down."
}
```

---

## 🧪 Testing

```bash
pytest tests/
```

Run with coverage:

```bash
coverage run -m pytest
coverage report
```

---

## 🐳 Docker

```bash
docker build -t aptiverse-ai .
docker run -p 8000:8000 aptiverse-ai
```

---

## 🔮 Future Directions

* Model self-evaluation and retraining with collected feedback
* Integration with GPT-based summarization + fine-tuned LLMs
* Integration with SA Dept. of Education curriculum database
* Voice-based input for diary & spoken test generation
* OpenAPI + gRPC hybrid model serving

---

## 🤝 Contributions

This project welcomes contributors passionate about:

* 🧠 Mental health and education
* 📚 NLP + ML for academic impact
* 🤖 Ethical AI systems for underserved communities

---

## 🛡️ Licensing

This repository is part of **Aptiverse Labs** and subject to internal licensing until public release.

---

## 🌱 Aptiverse: Grow Intelligence with Empathy

> *"We don’t just analyze learners. We uplift them."*

---