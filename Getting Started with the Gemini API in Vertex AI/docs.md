# Getting Started with the Gemini API in Vertex AI

Welcome to your first step into the world of Generative AI using Google's **Gemini API** on **Vertex AI**. This lab introduces the Gemini API and teaches you how to interact with it using simple prompts to build intelligent applications.

---

## 🎯 Objectives

- Learn how to authenticate and access the Gemini API.
- Understand how to send prompts and receive responses using Vertex AI.
- Explore the power of text generation for various use cases.
- Interact with Gemini via HTTP requests using `cURL`.

---

## 🧰 Prerequisites

- A Google Cloud project with Vertex AI API enabled.
- `gcloud` CLI installed and authenticated.
- Basic knowledge of terminal commands and `cURL`.

---

## 📌 Key Concepts

### 🔐 Authentication

Before making any API requests, you need to obtain an access token:

```bash
gcloud auth print-access-token
```

---

### 📨 Send a Prompt to Gemini

Use `cURL` to send a simple prompt to Gemini via Vertex AI:

```bash
curl \
  -X POST \
  -H "Authorization: Bearer $(gcloud auth print-access-token)" \
  -H "Content-Type: application/json" \
  https://us-central1-aiplatform.googleapis.com/v1/projects/YOUR_PROJECT_ID/locations/us-central1/publishers/google/models/gemini-1.0-pro:predict \
  -d '{
    "instances": [
      { "prompt": "Write a short story about a dragon who learns to dance." }
    ],
    "parameters": {
      "temperature": 0.7,
      "maxOutputTokens": 256
    }
  }'
```

Replace `YOUR_PROJECT_ID` with your actual Google Cloud project ID.

---

### 💬 Sample Response

The model returns a text-based response such as:

```json
{
  "predictions": [
    {
      "content": "Once upon a time, a clumsy dragon named Dazzy discovered a magical music box..."
    }
  ]
}
```

---

## 🌐 API Endpoint

Gemini API requests go to:

```
https://us-central1-aiplatform.googleapis.com/v1/projects/PROJECT_ID/locations/LOCATION/publishers/google/models/gemini-1.0-pro:predict
```

---

## 📁 GitHub Repository

All code and labs are hosted here:  
🔗 [Develop-GenAI-Apps-with-Gemini-and-Streamlit GitHub Repo](https://github.com/Yash22222/Develop-GenAI-Apps-with-Gemini-and-Streamlit)

---
