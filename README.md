# ar-math-solver
# 📐 AR Math Equation Solver — Real-Time AI + Augmented Reality

Point your camera at a math equation. Watch the solution appear in your physical space.

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-latest-teal)
![OpenCV](https://img.shields.io/badge/OpenCV-latest-green?logo=opencv)
![AR.js](https://img.shields.io/badge/AR.js-Web_AR-purple)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 🧠 What It Does

A real-time AI system that:
1. Accepts an image of a math equation (upload or camera)
2. Preprocesses it using computer vision (OpenCV)
3. Extracts the equation using deep learning OCR (Pix2Tex → LaTeX)
4. Solves it step-by-step using a locally hosted LLM (WizardMath 13B)
5. Streams the solution token-by-token via FastAPI
6. Visualizes the answer in **Augmented Reality** using AR.js + A-Frame

---

## ✨ Features

- **Smart Image Preprocessing** — CLAHE, bilateral filtering, deskewing, sharpening via OpenCV
- **LaTeX OCR** — Pix2Tex extracts complex mathematical expressions (fractions, integrals, exponents)
- **LLM-Powered Solving** — WizardMath 13B generates human-readable step-by-step solutions
- **Real-Time Streaming** — FastAPI streams solution tokens as they're generated
- **3 Interaction Modes**:
  - 📁 **Upload Mode** — Upload an image via web interface
  - 📍 **AR Marker Mode** — Solutions anchored to a printed marker in physical space
  - 🌐 **AR Markerless Mode** — Place solutions anywhere in your environment
- **Cross-Platform** — Works on desktop, tablet, and mobile browsers

---

## 🏗️ Architecture

```
Image Input (Upload / Camera)
         │
         ▼
┌─────────────────────────────┐
│   OpenCV Preprocessing       │
│   Grayscale → CLAHE →        │
│   Bilateral Filter →         │
│   Sharpen → Deskew           │
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   Pix2Tex LaTeX OCR          │
│   Image → LaTeX Expression   │
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   WizardMath LLM (via Ollama)│
│   LaTeX → Step-by-Step Soln  │
│   Streamed token by token    │
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   AR Visualization           │
│   AR.js + A-Frame (WebAR)    │
└─────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Image Preprocessing | OpenCV, NumPy |
| OCR Engine | Pix2Tex (LaTeX OCR) |
| LLM Solver | WizardMath 13B via Ollama |
| Backend API | FastAPI (async streaming) |
| AR Visualization | AR.js, A-Frame |
| Frontend | HTML5, JavaScript |
| Database | PostgreSQL (session & history) |
| Language | Python 3.10+ |

---

## 📁 Project Structure

```
ar-math-solver/
├── backend/
│   ├── main.py              # FastAPI entry point + streaming
│   ├── preprocessor.py      # OpenCV image preprocessing pipeline
│   ├── ocr.py               # Pix2Tex LaTeX extraction
│   ├── solver.py            # WizardMath LLM integration (Ollama)
│   └── database.py          # PostgreSQL session management
├── frontend/
│   ├── index.html           # Upload mode interface
│   ├── ar-marker.html       # Marker-based AR mode
│   ├── ar-markerless.html   # Markerless AR mode
│   └── assets/
│       └── testing.patt     # AR marker pattern file
├── tests/
│   └── test_pipeline.py
├── requirements.txt
├── .env.example
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- [Ollama](https://ollama.ai/) installed locally
- WizardMath model: `ollama pull wizardmath`
- PostgreSQL running locally

```bash
# Clone the repo
git clone https://github.com/yourusername/ar-math-solver.git
cd ar-math-solver

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env

# Start the FastAPI backend
uvicorn backend.main:app --reload

# Open frontend/index.html in your browser
```

---

## 🎯 Supported Equation Types

- ✅ Linear & quadratic equations
- ✅ Fractions, roots, and exponents
- ✅ Trigonometric expressions
- ✅ Integrals and derivatives (calculus)
- ✅ Summations and series
- ✅ Handwritten equations (with sufficient clarity)

---

## 📊 Key Results

- ✅ Real-time solution streaming via FastAPI async responses
- ✅ High OCR accuracy on printed equations with preprocessing pipeline
- ✅ Cross-platform AR visualization on mobile and desktop browsers
- ✅ Step-by-step solutions matching human tutor quality

---

## 🔮 Future Improvements

- [ ] MathPix integration for improved handwriting recognition
- [ ] Offline solving via SymPy (no LLM dependency)
- [ ] Real-time object tracking for dynamic AR
- [ ] Multi-language solution output

---


