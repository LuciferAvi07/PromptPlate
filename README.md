# PromptPlate

> Setup & Installation Guide — step-by-step instructions to configure and run PromptPlate locally.

## Table of Contents

1. [Prerequisites](#1-prerequisites)
2. [Clone the Project](#2-clone-or-enter-project-directory)
3. [Virtual Environment](#3-create--activate-virtual-environment)
4. [Install Dependencies](#4-install-dependencies)
5. [Twilio WhatsApp Sandbox](#5-activate-the-twilio-whatsapp-sandbox)
6. [API Secrets](#6-configure-api-secrets)
7. [Run the Application](#7-run-the-application)

---

## 1. Prerequisites

- **Python 3.9+** installed
- **Gemini API Key** — generate one via [Google AI Studio](https://aistudio.google.com/)
- **Twilio Account** — free sandbox access via [Twilio](https://www.twilio.com/try-twilio)

## 2. Clone or Enter Project Directory

```bash
git clone https://github.com/<your-username>/promptplate.git
cd promptplate
```

## 3. Create & Activate Virtual Environment

### Windows (PowerShell)

```powershell
python -m venv venv
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\venv\Scripts\Activate.ps1
```

### Windows (Command Prompt)

```bat
python -m venv venv
venv\Scripts\activate.bat
```

### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

## 4. Install Dependencies

Make sure your virtual environment is active (indicated by `(venv)` in your terminal), then run:

```bash
pip install -r requirements.txt
```

Required packages inside `requirements.txt`:

```text
streamlit
google-genai
twilio
```

## 5. Activate the Twilio WhatsApp Sandbox

1. Open the [Twilio Console](https://console.twilio.com/).
2. Navigate to **Messaging → Try it out → Send a WhatsApp message**.
3. Note the Twilio sandbox phone number (e.g., `whatsapp:+14155238886`) and the sandbox join phrase (e.g., `join happy-tiger`).
4. From your test phone's WhatsApp, send that exact join phrase to the Twilio number.
5. Wait for the automated reply confirming your sandbox session is linked.

## 6. Configure API Secrets

1. Create a `.streamlit` folder in your project root:

   ```bash
   mkdir .streamlit
   ```

2. Create `secrets.toml` inside `.streamlit`:

   - **Windows:** `notepad .streamlit\secrets.toml`
   - **macOS / Linux:** `nano .streamlit/secrets.toml`

3. Add your credentials:

   ```toml
   GEMINI_API_KEY = "your_google_ai_studio_key_here"
   TWILIO_ACCOUNT_SID = "your_twilio_account_sid_here"
   TWILIO_AUTH_TOKEN = "your_twilio_auth_token_here"
   TWILIO_WHATSAPP_FROM = "whatsapp:+14155238886"
   ```

4. Verify that `.streamlit/secrets.toml` is included in your `.gitignore`:

   ```gitignore
   .streamlit/secrets.toml
   venv/
   __pycache__/
   *.pyc
   ```

> ⚠️ **Never commit `secrets.toml` or share your API keys / Twilio auth token publicly.**

## 7. Run the Application

Launch the local Streamlit server:

```bash
streamlit run app.py
```

Open [http://localhost:8501](http://localhost:8501) in your browser, enter your name and phone number with country code (e.g., `+91XXXXXXXXXX`), and begin logging meals.
