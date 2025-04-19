#  Getting Started with the Gemini API in Vertex AI with cURL




This introduces how to interact with Google's Gemini API using simple `cURL` commands. Instead of using client libraries or SDKs, this approach allows you to make direct HTTP requests to the Vertex AI endpoints — great for quick testing or integration into lightweight environments.

---

## 🚀 Objectives

- Understand how to authenticate and make secure API calls to Gemini using `cURL`.
- Learn how to send prompts and receive completions directly from the Gemini model.
- Experiment with different parameters for controlling generation behavior.

---

## 🧰 Prerequisites

- A Google Cloud Project with Vertex AI API enabled.
- An access token generated using `gcloud auth print-access-token`.
- Basic terminal and cURL knowledge.

---

## ⚙️ Steps

### 1. Set Environment Variables

```bash
export PROJECT_ID=$(gcloud config get-value project)
export ACCESS_TOKEN=$(gcloud auth print-access-token)
```

---

### 2. Prepare a Sample Prompt

```json
{
  "contents": [
    {
      "parts": [
        {
          "text": "List five interesting facts about artificial intelligence."
        }
      ]
    }
  ]
}
```

Save this as `prompt.json`.

---

### 3. Make the cURL Request

```bash
curl \
  -X POST \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  https://us-central1-aiplatform.googleapis.com/v1/projects/$PROJECT_ID/locations/us-central1/publishers/google/models/gemini-1.0-pro:generateContent \
  -d @prompt.json
```

---

### 4. View the Response

You’ll receive a JSON response with generated content from the Gemini model. You can parse it or save it to a file.

---

## 📌 Notes

- Replace the model endpoint to use different Gemini versions like `gemini-1.5-pro` if needed.
- You can experiment with additional fields like `safetySettings`, `temperature`, and `topK` in the request body.
- Ideal for automated tasks, command-line exploration, and integrating GenAI into shell scripts.

---

## 📁 GitHub Repository

🔗 [View on GitHub](https://github.com/Yash22222/Develop-GenAI-Apps-with-Gemini-and-Streamlit)

---

