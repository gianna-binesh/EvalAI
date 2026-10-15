# EvalAI
EvalAI is an intelligent assessment framework designed to evaluate handwritten examination responses using multimodal AI, semantic evaluation, and explainable scoring. The current prototype was developed using Base44, with the research methodology and evaluation framework designed around human-in-the-loop assessment.

🚀 Key Features

* **Handwritten OCR Extraction:** Specialized processing pipelines for parsing complex STEM handwriting, mathematical symbols, and diagrams.
* **Intelligent Rubric Alignment:** Multi-step grading agent that maps student answers to granular, multi-point grading rubrics.
* **Confidence-Scored Grading:** Every graded question receives an AI confidence metric.
* **Human-in-the-Loop Dashboard:** Low-confidence evaluations, edge cases, and contested grades are automatically routed to a human reviewer for manual verification.
* **Analytics & Insights:** Instant metrics highlighting class performance, common misconceptions, and item analysis.

---

## 🏗️ System Workflow

```text
       ┌────────────────────────┐
       │  Handwritten STEM Page │
       └───────────┬────────────┘
                   │
                   ▼
     ┌────────────────────────────┐
     │ OCR & Symbol Recognition  │
     └───────────┬────────────┘
                   │
                   ▼
     ┌────────────────────────────┐
     │   AI Rubric Evaluation     │
     └───────────┬────────────┘
                   │
            [Confidence Score]
            /               \
     High Confidence     Low Confidence
          /                   \
         ▼                     ▼
┌─────────────────┐   ┌───────────────────────────┐
│ Auto-Save Grade │   │ Human Review Dashboard   │
└─────────────────┘   └─────────────┬─────────────┘
                                    │ (Human Adjustments)
                                    ▼
                          ┌──────────────────┐
                          │ Finalized Grade  │
                          └──────────────────┘
```

---

## 🛠️ Tech Stack (Suggested)

* **Backend Engine:** Python, FastAPI / Django, OpenCV, PyTorch / HuggingFace
* **LLM / OCR Layer:** OpenAI GPT-4o / Claude 3.5 Sonnet / AWS Textract / Custom TrOCR
* **Frontend Dashboard:** React.js / Next.js, Tailwind CSS
* **Database & Queue:** PostgreSQL, Redis, Celery (for asynchronous sheet processing)

---

## ⚙️ Quick Start Setup

### Prerequisites
* Python 3.10+
* Node.js 18+ (if running the web dashboard)
* Docker (Optional but recommended)

### 1. Backend Installation
```bash
# Clone the repository
git clone https://github.com/your-username/evalai.git
cd evalai/backend

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`

# Install dependencies
pip install -r requirements.txt

# Run migrations and start server
python manage.py migrate  # or uvicorn main:app --reload
```

### 2. Frontend Interface Setup
```bash
cd ../frontend
npm install
npm run dev
```

---

## 📝 Grading Rubric Configuration

Define your rubrics in JSON or YAML formats within the system to map points to specific structural milestones:

```json
{
  "question_1": {
    "total_points": 5,
    "criteria": [
      {"points": 2, "condition": "Correctly isolates the variable 'x'."},
      {"points": 2, "condition": "Applies correct integration steps."},
      {"points": 1, "condition": "Final numerical value matches and contains units."}
    ]
  }
}
```

---

## 🤝 Contributing

Contributions to improve OCR accuracy, rubric logic, or the human validation portal are welcome! Please open an issue or submit a pull request.

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
