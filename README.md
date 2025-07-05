# 🧠 Aptiverse AI Models – FastAPI Microservice for Education-Powered Machine Learning

The **Aptiverse AI Models** service is a collection of **subject-specific and task-specific machine learning models** served via a **FastAPI** backend. It acts as the brain behind Aptiverse’s personalized learning recommendations, emotion detection, summarization tools, and academic analysis.

This microservice is decoupled from the main `.NET API` and designed to be triggered via **HTTP** or **message queues** (RabbitMQ) via the **Aptiverse Worker**.

---

## 🧠 What It Does

* 🔍 **Emotion Analysis**
  Analyzes student journal entries and extracts emotional sentiment (`["stressed", "motivated"]`).

* 📚 **Smart Summarization**
  Generates concise summaries of academic content.

* 📘 **Subject-Specific Insight Models**
  Custom classifiers for subjects like Math, Biology, and Physics to analyze test answers and detect weak areas.

* 🎓 **Study Plan Generator**
  Suggests optimized study paths based on performance and learning style.

* 🧠 **Psychological Insights**
  Uses NLP and behavioral analysis to give feedback on student habits.

---

## 🛠️ Tech Stack

| Component           | Technology                                      |
| ------------------- | ----------------------------------------------- |
| API Framework       | FastAPI                                         |
| ML Libraries        | scikit-learn, PyTorch, TensorFlow, Transformers |
| Data Processing     | pandas, NumPy, NLTK, spaCy                      |
| API Communication   | JSON over HTTP                                  |
| Model Serialization | joblib / pickle / TorchScript                   |
| Dev Tools           | Uvicorn, Pydantic, Docker                       |

---

## 📁 Project Structure

```
aptiverse_ai/
├── main.py                      → FastAPI entrypoint
├── models/
│   ├── emotion_model.py         → Loads sentiment model
│   ├── summarizer.py            → Summarization logic
│   └── subject_models/          → Per-subject ML models
├── services/
│   ├── preprocess.py            → Text cleaning, tokenization
│   ├── planner.py               → Study plan logic
│   └── insights.py              → Analysis services
├── schemas/
│   └── request_response.py      → Pydantic models
├── tests/
│   └── test_models.py           → Unit tests
└── requirements.txt             → Python dependencies
```

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/your-org/aptiverse-ai.git
cd aptiverse-ai
```

### 2. Set up a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 3. Start the FastAPI server

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

### 4. Test in browser or with Postman

Navigate to:
👉 `http://localhost:8000/docs` — FastAPI’s interactive Swagger UI

---

## 📬 API Endpoints (Examples)

| Endpoint           | Method | Description                          |
| ------------------ | ------ | ------------------------------------ |
| `/analyze-emotion` | POST   | Detects emotion from journal entry   |
| `/summarize`       | POST   | Returns summarized text              |
| `/subject/analyze` | POST   | Evaluates answer, returns weak areas |
| `/study-plan`      | POST   | Suggests study strategy              |

#### Sample Payload (for `/summarize`)

```json
{
  "text": "Photosynthesis is the process by which green plants..."
}
```

#### Response

```json
{
  "summary": "Photosynthesis allows green plants to convert sunlight into energy."
}
```

---

## 🧪 Testing

```bash
pytest tests/
```

Or run with test coverage:

```bash
coverage run -m pytest
coverage report
```

---

## 🐳 Docker Support

```bash
docker build -t aptiverse-ai .
docker run -p 8000:8000 aptiverse-ai
```

---

## 🔌 Integration

This service is called by:

* ✅ **Aptiverse Worker** via HTTP
* 🔄 (Optionally) directly from `.NET API` via RestSharp
* ⚙️ Designed for future gRPC or WebSocket compatibility

---

## 📈 Future Enhancements

* Support batch processing and model caching
* Add gRPC endpoints for high-speed inference
* Connect to vector databases (Pinecone, Weaviate) for semantic search
* Self-healing model pipelines using monitoring and auto-retraining
* Student persona embeddings for long-term personalized adaptation

---

## 👨‍🔬 Model Training

This repo is focused on **inference**, but training code may live in a separate `aptiverse-training` repo (or `/notebooks` folder), using:

* Custom datasets (student essays, exam history)
* Pretrained transformers fine-tuned for South African curricula
* Data augmentation pipelines

---

## 🤝 Contribution

PRs are welcome! If you're into:

* AI for education
* NLP model optimization
* Ethical & inclusive AI

Then this project is for you. Let's build something that uplifts students through intelligence and empathy.

---

## 🪪 License

This microservice is part of **Aptiverse Labs**. Licensing terms will be provided upon request or during future public releases.

---

## 💡 Aptiverse: Empowering Students With Intelligence and Insight

> *"We don't just grade students. We grow them."*

---
