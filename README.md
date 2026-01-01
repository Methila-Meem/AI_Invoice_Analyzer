# 🧾 AI Invoice Analyzer

---

## 🚀 Project Overview

AI Invoice Analyzer is an end-to-end document intelligence prototype built in Google Colab that extracts structured invoice data from images and PDFs using OCR + a local Large Language Model.

This project demonstrates how traditional OCR pipelines can be augmented with LLM reasoning to convert noisy, unstructured documents into validated, machine-readable JSON — a common real-world problem in finance and operations.

⚠️ Current status: Notebook-based prototype (Colab)
🚧 Designed with a clear path toward productionization

---

## 🧩 What Problem Does This Solve?

Manual invoice processing is:

- Time-consuming

- Error-prone

- Expensive at scale

This system automates:

- Invoice data extraction

- Structural normalization

- Logical validation (totals, dates)

All without relying on cloud LLM APIs, making it suitable for privacy-sensitive environments.

---

## 🧠 Key Capabilities

📄 Accepts invoice images and PDFs

🔍 OCR extraction using Tesseract

🧠 Local LLM (Ollama) for structured JSON extraction

📋 Extracted fields:

- Vendor name

- Invoice number

- Invoice date & due date

- Subtotal, tax, total

- Currency

✅ Automatic validation:

- Total ≈ Subtotal + Tax

- Due date > Invoice date

- Invoice number format checks

🌐 Interactive Gradio web interface

🔐 Fully local LLM inference (no OpenAI / cloud APIs)

---

## 🏗️ System Architecture (Conceptual)

```
Invoice (PDF / Image)
        │
        ▼
 Image Preprocessing
 (Resize, optimize)
        │
        ▼
   OCR Engine
 (Tesseract)
        │
        ▼
 Extracted Raw Text
        │
        ▼
 Local LLM (Ollama)
 (Prompt-engineered
 JSON extraction)
        │
        ▼
 Structured Invoice Data
        │
        ▼
 Business Rule Validation
        │
        ▼
 JSON Output + UI Display

```

---

## 🛠️ Tech Stack

| Category         | Tools                              |
| ---------------- | ---------------------------------- |
| Language         | Python                             |
| Notebook         | Google Colab                       |
| OCR              | Tesseract                          |
| LLM              | Ollama (LLaMA 3.2 / Phi-3 / Gemma) |
| PDF Handling     | pdf2image                          |
| Image Processing | Pillow                             |
| UI               | Gradio                             |
| Validation       | Custom rule-based logic            |

---
## ▶️ How to Run (Google Colab)

1️⃣ Open the notebook:

```
notebook/AI_Invoice_Analyzer.ipynb
```

2️⃣ Run cells top to bottom:

- Installs system dependencies

- Starts Ollama

- Pulls LLM model

- Launches Gradio UI

3️⃣ Upload an invoice:

- File types: .jpg, .png, or .pdf

4️⃣ View:

- Structured summary

- Full validated JSON output

⚠️ First run may take 30–60 seconds due to model loading.

---

## 📊 Example Output

```
{
  "vendor_name": "ABC Supplies Ltd",
  "invoice_number": "INV-2024-001",
  "invoice_date": "2024-10-01",
  "due_date": "2024-10-30",
  "subtotal": 950.0,
  "tax": 50.0,
  "total": 1000.0,
  "currency": "USD"
}
```
---

## 🧠 Engineering & Learning Highlights

- Designed a modular AI pipeline inside a notebook:

  - Preprocessing

  - OCR

  - LLM extraction

  - Validation

- Prompt-engineered strict JSON-only LLM responses

- Implemented confidence scoring and validation logic

- Managed local LLM lifecycle inside Colab

- Focused on production constraints:

  - Latency

  - Validation

  - Error handling

  - Privacy

---

## 🔮 Roadmap to Production

This notebook is intentionally structured to be split into modules:

- Refactor into Python packages

- Expose FastAPI REST endpoints

- Add batch invoice processing

- Dockerize OCR + LLM services

- Persist results to a database

- Deploy on VM / on-prem environment

---
