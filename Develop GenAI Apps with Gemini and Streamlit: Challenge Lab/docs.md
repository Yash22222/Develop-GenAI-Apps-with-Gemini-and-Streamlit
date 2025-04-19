# Develop GenAI Apps with Gemini and Streamlit – Challenge Lab

## 📘 Scenario

You are a **Chef** working in a restaurant that specializes in **Japanese cuisine**. Your customers have specific health and dietary requirements. You want to create a **GenAI-powered application** to help generate **Japanese recipes** that are:

- **Low in sodium**
- **Peanut allergy-safe**
- Incorporate available ingredients like **ahi tuna, fresh ginger, and edamame**
- Tailored to a **red wine** preference

The app should also provide:
- Step-by-step **preparation instructions**
- **Time to prepare**
- A suitable **wine pairing**
- **Calorie count**
- **Nutritional facts**

---

## 🎯 Objective

Build and deploy an application that:

1. Accepts user input (ingredients, dietary restrictions, preferences)
2. Uses **Gemini API** to generate meal recommendations dynamically
3. Provides:
   - Recipe title
   - Ingredients
   - Step-by-step instructions
   - Preparation time
   - Wine pairing
   - Calories and nutritional facts
4. Is built with **Streamlit**
5. Is deployed using **Cloud Run**

---

## 🛠️ Task Breakdown

### ✅ Task 1: Design the Prompt

Design a clear and structured prompt that will be sent to the **Gemini model**. The prompt should include:

- Ingredients (ahi tuna, fresh ginger, edamame)
- Restrictions (low sodium, peanut-free)
- Preference (Japanese cuisine, red wine pairing)
- Output expectations (title, instructions, wine, nutrition)

### ✅ Task 2: Build the Streamlit App

Create a `streamlit_app.py` with:

- A sidebar for user input (e.g., ingredients, preferences)
- A `generate_recipe()` function to call Gemini with the designed prompt
- A results section to display the recipe nicely formatted

### ✅ Task 3: Integrate Gemini

Use the **Vertex AI SDK** or **REST API** to connect with **Gemini**:

```python
from vertexai.generative_models import GenerativeModel

model = GenerativeModel("gemini-1.0-pro")
response = model.generate_content(prompt)
```

### ✅ Task 4: Deploy with Cloud Run

1. Create a `Dockerfile` to containerize the Streamlit app.
2. Deploy the app to Cloud Run with:

```bash
gcloud builds submit --tag gcr.io/YOUR_PROJECT/recipe-app
gcloud run deploy recipe-app --image gcr.io/YOUR_PROJECT/recipe-app --platform managed
```

---

## 🧪 Example Prompt for Gemini

```
I am a Chef. I need to create Japanese recipes for customers who want low sodium meals. However, I do not want to include recipes that use ingredients associated with a peanuts food allergy. I have ahi tuna, fresh ginger, and edamame in my kitchen and other ingredients. The customer wine preference is red. Please provide some meal recommendations.

For each recommendation, include:
- Title
- Preparation instructions
- Time to prepare
- Wine pairing
- Calories
- Nutritional facts
```

---

## 📦 Deliverables

- A working Streamlit app
- Gemini integration for intelligent recipe generation
- Successful deployment on Cloud Run
- Functional user interface for input and output
- Well-structured responses including recipe, wine pairing, and nutritional info

---

## 🏁 Completion Criteria

- ✅ Prompt dynamically adapts to user inputs
- ✅ Recipe excludes peanut ingredients
- ✅ Response includes instructions, time, wine, and nutritional facts
- ✅ Streamlit app is deployed on Cloud Run and accessible via URL

---
