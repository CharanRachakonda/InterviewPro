# 🚀 InterviewPro: AI-Powered Interview Coach

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Framework-Flask-lightgrey.svg)](https://flask.palletsprojects.com/)
[![Gemini](https://img.shields.io/badge/AI-Google%20Gemini%202.0-orange.svg)](https://aistudio.google.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

**InterviewPro** is a comprehensive AI-driven platform designed to bridge the gap between job applications and successful hires. By leveraging Large Language Models (LLMs) and Speech-to-Text technology, it provides a personalized, high-stakes simulation environment for job seekers.

[**Features**](#-features) • [**Tech Stack**](#-tech-stack) • [**Getting Started**](#-getting-started) • [**Workflow**](#-how-it-works) • [**API Reference**](#-api-routes)

---

## ✨ Features

### 📄 Intelligent Resume Analysis
Upload your resume (PDF/DOCX). Our system uses **spaCy NLP** and **Gemini 2.0** to extract technical skills, leadership experience, and project history to generate questions a real recruiter would ask.

### 🎯 Job-Specific Practice
Don't have a resume handy? Input a job title and description. The AI generates targeted **Behavioral**, **Technical**, and **Situational** questions based on industry standards.

### 🎙️ Voice-Enabled Mock Interviews
*   **Real-time Transcription:** Speak your answers naturally. We use **Hugging Face Whisper Large v3 Turbo** for near-instant speech-to-text.
*   **Audio Processing:** Integrated with `pydub` and `FFmpeg` for seamless audio handling.

### 📊 AI-Driven Evaluation & Feedback
*   **Scoring (1–10):** Get instant quantitative metrics on technical accuracy and clarity.
*   **STAR Method Alignment:** AI evaluates behavioral answers based on the Situation, Task, Action, and Result framework.
*   **Model Answers:** Struggling with a question? Generate high-quality sample answers on the fly.

---

## 🛠️ Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Frontend** | Jinja2 Templates, Tailwind CSS (optional suggestion), JavaScript (Web Audio API) |
| **Backend** | Flask (Python) |
| **Database** | MongoDB (PyMongo) |
| **LLM Orchestration** | LangChain Core & Google Gemini 2.0 Flash |
| **Speech-to-Text** | Hugging Face Inference API (Whisper Large v3 Turbo) |
| **NLP & Parsing** | spaCy (`en_core_web_sm`), PyPDF2, python-docx |
| **Audio Pipeline** | pydub, FFmpeg |

---

## 📂 Project Structure

```bash
InterviewPro/
├── app.py                # Flask application & Route Handlers
├── requirements.txt      # Project dependencies
├── .env.example          # Template for environment variables
├── static/
│   ├── css/              # Frontend styling
│   └── js/               # Audio recording & AJAX logic
├── templates/            # Jinja2 HTML templates
└── utils/
    ├── resume_parser.py  # NLP-based detail extraction
    └── question_gen.py   # AI prompt engineering & evaluation logic
```

---

## 🚀 Getting Started

### Prerequisites
*   Python 3.9 or higher
*   [FFmpeg](https://ffmpeg.org/download.html) installed on your system (Required for audio)
*   MongoDB (Local or Atlas)

### 1. Installation
```bash
git clone https://github.com/yourusername/InterviewPro.git
cd InterviewPro
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

### 2. Environment Configuration
Create a `.env` file in the root directory:
```env
# API Keys
GOOGLE_API_KEY=your_gemini_api_key_here
HF_API_TOKEN=your_huggingface_token_here

# Database
MONGO_URI=mongodb://localhost:27017
SECRET_KEY=your_flask_secret_key
```

### 3. Running the App
```bash
python app.py
```
Visit `http://localhost:5000` in your browser.

---

## 🔄 How It Works

1.  **Parsing Engine:** When a resume is uploaded, `spaCy` identifies Named Entities (NER) like programming languages and job titles.
2.  **Prompt Engineering:** We use **LangChain** to wrap user data into structured prompts:
    *   *"Act as a Senior Engineer at Google. Based on this resume: [Resume Text], ask 3 hard technical questions."*
3.  **Inference:** Gemini 2.0 Flash processes the request, returning a structured JSON of questions.
4.  **Audio Loop:** The browser captures audio $\rightarrow$ `pydub` converts it to the correct sample rate $\rightarrow$ Whisper API returns the transcript.
5.  **Analytics:** The final report aggregates scores to show progress over time via the **Interview History** dashboard.

---

## 🛣️ API Routes

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/app` | Processes resume and initializes session. |
| `POST` | `/transcribe-audio` | Accepts Blob audio, returns string text. |
| `POST` | `/evaluate-interview` | Triggers LLM evaluation of all session answers. |
| `POST` | `/generate-answer` | Generates a "Model Answer" for a specific question. |

---

## 🤝 Contributing

Contributions make the open-source community an amazing place to learn and create.
1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License
Distributed under the MIT License. See `LICENSE` for more information.

---
**Disclaimer:** *InterviewPro uses Google Gemini 2.0. AI-generated feedback should be used as a guide and not as professional career advice.*

---

### Key Improvements Made:
1.  **Visual Interest:** Added badges and tables to make the technical details "scannable."
2.  **Logical Grouping:** Created a "Workflow" section to explain *how* the AI works, which is great for recruiters or other developers.
3.  **Security/Best Practices:** Added a section for `.env` configuration (instead of just exporting) and a `.env.example` reference.
4.  **Professional Tone:** Added "Contributing" and "Disclaimer" sections.
5.  **Tech Depth:** Mentioned specific concepts like NER (Named Entity Recognition) and the STAR method for behavioral questions.
