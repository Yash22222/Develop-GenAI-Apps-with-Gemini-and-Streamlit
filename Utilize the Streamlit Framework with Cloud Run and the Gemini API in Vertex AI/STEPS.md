```txt
git clone https://github.com/GoogleCloudPlatform/generative-ai.git --depth=1
```

```txt
cd generative-ai/gemini/sample-apps/gemini-streamlit-cloudrun
```

```txt
python3 -m venv gemini-streamlit
source gemini-streamlit/bin/activate
pip install -r requirements.txt
```

```txt
GOOGLE_CLOUD_PROJECT='Apna Wala Dal'
GOOGLE_CLOUD_REGION=' '
```

```txt
AR_REPO='gemini-repo'
SERVICE_NAME='gemini-streamlit-app' 
gcloud artifacts repositories create "$AR_REPO" --location="$GOOGLE_CLOUD_REGION" --repository-format=Docker
gcloud builds submit --tag "$GOOGLE_CLOUD_REGION-docker.pkg.dev/$GOOGLE_CLOUD_PROJECT/$AR_REPO/$SERVICE_NAME"
```

```txt
gcloud run deploy "$SERVICE_NAME" \
  --port=8080 \
  --image="$GOOGLE_CLOUD_REGION-docker.pkg.dev/$GOOGLE_CLOUD_PROJECT/$AR_REPO/$SERVICE_NAME" \
  --allow-unauthenticated \
  --region=$GOOGLE_CLOUD_REGION \
  --platform=managed  \
  --project=$GOOGLE_CLOUD_PROJECT \
  --set-env-vars=GOOGLE_CLOUD_PROJECT=$GOOGLE_CLOUD_PROJECT,GOOGLE_CLOUD_REGION=$GOOGLE_CLOUD_REGION
```
