# Lab 4:- Utilize the Streamlit Framework with Cloud Run and the Gemini API in Vertex AI

Lets See to combine the power of **Streamlit**, **Cloud Run**, and **Gemini API** in **Vertex AI** to build and deploy a real-time GenAI application. This enables you to quickly prototype and serve LLM-based apps on the web.

---

## 🎯 Objectives

- Build a simple interactive GenAI application using Streamlit.
- Deploy your Streamlit app on Google Cloud Run.
- Integrate the app with Gemini API (Vertex AI) to handle user prompts.
- Learn how to connect frontend interactions with LLM backends effectively.

---

## 🧰 Prerequisites

- Google Cloud Project with Vertex AI and Cloud Run APIs enabled.
- Basic Python and Streamlit knowledge.
- Google Cloud SDK installed and authenticated.

---

## 🏗️ Step-by-Step Guide

### 1️⃣ Create a Streamlit App

Start by writing your `app.py` file using Streamlit to capture user input and display Gemini-generated responses.

```python
import streamlit as st
import vertexai
from vertexai.generative_models import GenerativeModel

st.title("💬 Chat with Gemini via Vertex AI")

prompt = st.text_area("Enter your prompt:")
submit = st.button("Send to Gemini")

if submit and prompt:
    vertexai.init(project="YOUR_PROJECT_ID", location="us-central1")
    model = GenerativeModel("gemini-1.0-pro")
    response = model.generate_content(prompt)
    st.markdown("### Response:")
    st.write(response.text)
```

---

### 2️⃣ Create a `requirements.txt`

```txt
streamlit
google-cloud-aiplatform
```

---

### 3️⃣ Create a Dockerfile

```dockerfile
FROM python:3.10

WORKDIR /app
COPY . .

RUN pip install -r requirements.txt

EXPOSE 8501

CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

---

### 4️⃣ Build and Deploy with Cloud Run

```bash
gcloud builds submit --tag gcr.io/YOUR_PROJECT_ID/genai-streamlit-app

gcloud run deploy genai-streamlit-app \
  --image gcr.io/YOUR_PROJECT_ID/genai-streamlit-app \
  --platform managed \
  --region us-central1 \
  --allow-unauthenticated
```

---

## 🌍 Access the App

Once deployed, Cloud Run provides a live URL to your GenAI-powered Streamlit app!

---

## ✅ What You Learned

- How to build a Streamlit UI to interact with Gemini API.
- How to containerize and deploy Streamlit apps using Docker.
- How to use Cloud Run for scalable, serverless hosting of your AI apps.
- Practical integration of frontend and GenAI backend.

---

## 📁 GitHub Repository

Explore the code here:  
🔗 [Develop-GenAI-Apps-with-Gemini-and-Streamlit](https://github.com/Yash22222/Develop-GenAI-Apps-with-Gemini-and-Streamlit)

---
