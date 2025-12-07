# 🦈 Shark Tank Pitch Analyzer

### A Multimodal Audio + NLP System for Automated Pitch Evaluation

This project implements an end-to-end **Shark Tank–style pitch evaluation system** using audio processing, speech transcription, semantic business analysis, and AI-generated investor feedback.

It analyzes both **how** a person speaks (delivery) and **what** they say (business content), then outputs a final investment recommendation with multi-persona shark feedback.

---

## 🚀 Features

### 🎤 **Pipeline 1 — Voice & Delivery Analysis (Audio ML)**

Extracts prosodic and acoustic features using **Librosa**:

* Pitch statistics (F0 mean, variability, range)
* RMS energy & vocal intensity
* Pauses & hesitation index
* Speaking rate (Words Per Minute)
* Filler word detection
* Confidence + clarity scoring

Produces a **Delivery Score (0–100)**.

---

### 📝 **Pipeline 2 — Content & Business Logic Analysis (NLP)**

Using Whisper ASR (optional) + NLP scoring methods:

* Problem clarity
* Product differentiation
* Business model robustness
* Market opportunity
* Competition awareness
* Revenue logic

Produces a **Business Score (0–100)**.

---

### 🦈 **Shark Panel Feedback Engine**

Simulates feedback from four investor personas:

* **Visionary Shark** – innovation focus
* **Finance Shark** – margins, CAC/LTV, unit economics
* **Customer Advocate** – user need & problem validation
* **Skeptic Shark** – risks & execution challenges

Outputs:

* Strengths & weaknesses
* Persona-wise verdicts (Invest / Need More Info / Not Invest)
* Final aggregated recommendation

---

## 📁 Repository Structure

```
SharkTankPitchAnalyzer/
│── audio_features.py
│── transcription.py
│── business_scoring.py
│── shark_panel.py
│── SharkTankPitchAnalyzer_notebook.ipynb   # runnable notebook
│── sample_audio/
│── pitch_report.json                       # sample output
│── README.md
│── requirements.txt
```

---

## ▶️ How to Run the Project

### **Option 1: Run in Google Colab (Recommended)**

1. Upload the notebook:
   `SharkTankPitchAnalyzer_notebook.ipynb`
2. Upload your pitch audio file (MP3/WAV).
3. Install dependencies:

   ```bash
   !pip install librosa soundfile sentence-transformers transformers torch matplotlib
   ```
4. (Optional) Enable Whisper ASR by uncommenting:

   ```python
   import whisper
   model = whisper.load_model("small")
   result = model.transcribe(AUDIO_PATH)
   ```
5. Run all cells → output:

   * Delivery Score
   * Business Score
   * Shark panel feedback
   * `pitch_report.json`

---

### **Option 2: Run Locally**

#### **1. Install dependencies**

```bash
pip install -r requirements.txt
```

#### **2. Add your audio file**

Place it inside the project folder and update:

```python
AUDIO_PATH = "your_audio_file.wav"
```

#### **3. Run the notebook**

```bash
jupyter notebook SharkTankPitchAnalyzer_notebook.ipynb
```

---

## 🧠 Technical Overview

### 🔊 **Audio Processing**

* `librosa.load()` for resampling
* `librosa.yin()` for pitch extraction
* STFT-based silence detection
* RMS energy for vocal intensity

### ✍️ **Content Scoring**

* Whisper transcription (optional)
* SentenceTransformer (`all-MiniLM-L6-v2`) for semantic similarity
* Fallback keyword-based scoring if embeddings unavailable

### 🦈 **Persona AI Feedback**

Templates included inside notebook.
Can be upgraded by calling OpenAI/GPT models to generate richer investor feedback automatically.

---

## 📌 Output Format (JSON)

Example structure of generated report:

```json
{
  "delivery_score": 72.5,
  "business_score": 78.3,
  "audio_features": {...},
  "business_components": {...},
  "shark_panel": {
    "Visionary": "...",
    "Finance": "...",
    "Customer Advocate": "...",
    "Skeptic": "..."
  }
}
```

---

## 📦 Requirements

```
librosa
numpy
soundfile
matplotlib
sentence-transformers
transformers
torch
whisper (optional)
```

Included in `requirements.txt`.

---

## 🧪 Future Improvements

* Real-time pitch evaluation dashboard
* Fine-tuned emotion recognition on IEMOCAP/CREMA-D
* A web UI using Flask/Streamlit
* Multi-language transcription support

---

## 👨‍💻 Author

Deepesh Lodhi
IIT Delhi

---

