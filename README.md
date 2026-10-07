# HealthLearn — Adaptive Health Literacy Engine

## 🏥 Healthcare Deployment

This engine is domain-agnostic. The healthcare deployment targets:
- **Patient health literacy** — patients understand their own conditions
- **Medical student assessment** — adaptive clinical knowledge testing  
- **Hospital staff training** — compliance and protocol quizzes

Topics: Diabetes Management · Medication Adherence · Nutrition & Diet · Warning Signs · Preventive Care · Emergency Response

---

## 🔬 Core Adaptive Engine

**IRT (Item Response Theory):** Rasch 1PL model estimates learner ability (θ) in real-time. Questions calibrated to optimal difficulty.

**DAG-Based Prerequisites:** NetworkX graphs ensure foundational health concepts are mastered before advanced disease management.

**Misconception Detection:** Wrong answers are classified and tagged, enabling targeted Socratic interventions.

**Spaced Repetition:** SM-2 algorithm schedules review of weak concepts based on forgetting curves.

## 🚀 Quick Start

```bash
# Backend
cd backend
pip install -r requirements.txt
uvicorn main:app --reload --port 8000

# Frontend  
cd frontend
npm install
npm run dev
```

## 📊 Architecture

```
frontend/ (Next.js)     → User interface
backend/ (FastAPI)      → API endpoints + business logic
  ├── agents/           → AI services (Groq LLaMA)
  ├── irt/              → Rasch model theta estimation
  ├── dag/              → Prerequisite topic graphs
  ├── mastery/          → Learning progress calculation
  └── misconceptions/   → Error pattern analysis
```

## 🩺 Healthcare Use Cases

**Patient Education:**
- Start with "Diabetes Management" → system generates subtopics → adaptive question difficulty
- Wrong answers trigger Socratic hints rather than showing correct answer immediately
- Misconceptions are classified (e.g., "confuses insulin types") for targeted remediation

**Medical Training:**
- Complex clinical scenarios with IRT-calibrated difficulty
- Prerequisite knowledge enforced (Basic Anatomy → Pathophysiology → Treatment)
- Real-time ability estimation guides curriculum pacing

**Quality Assurance:**
- Hospital staff compliance training with adaptive difficulty
- Identifies knowledge gaps across departments
- Spaced repetition ensures retention of critical protocols

## 🤖 AI Components

**Question Generation:** Groq LLaMA generates questions dynamically based on topic + difficulty + Bloom's taxonomy level

**Socratic Mode:** Fires when learner is confident (≥4/5) but wrong — provides guiding questions instead of answers

**Explanation Calibration:** AI explanations are tuned to learner's current theta (ability) level

## 📈 Differentiation

Unlike static healthcare training platforms, this engine:
- **Adapts in real-time** using psychometric models
- **Prevents cheating** through dynamic question generation  
- **Targets misconceptions** rather than just scoring correct/incorrect
- **Enforces prerequisites** via DAG backtracking when mastery drops
- **Scales efficiently** — same engine handles basic health literacy and advanced medical training

---

Built with FastAPI, Next.js, Groq LLaMA, NetworkX, and SQLAlchemy.