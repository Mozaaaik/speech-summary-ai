# 🎙️ Speech Summary AI

A web application that lets you **upload an audio file**, transcribe it to text with Google Speech‑to‑Text, **summarize** the transcript using an AI model (OpenAI), and then **synthesize** the summary back to speech.

---

<p align="center">
  <img src="https://i.imgur.com/Fqi8Xb0.png" alt="App Screenshot" width="800"/>
</p>

---  

## 🛠️ Features

- **Audio Upload**  
  Select any local audio file (`.mp3`, `.wav`, etc.) from your machine.  
- **Speech → Text**  
  Automatically convert speech to raw text using Google Cloud Speech‑to‑Text.  
- **Text Summarization**  
  Generate a concise, human‑readable summary via OpenAI’s language model.  
- **Summary → Speech**  
  Synthesize the AI summary back into an audio file with Google Text‑to‑Speech.  
- **Play & Download**  
  Stream the generated audio in‑browser or download it locally.

## 🚀 Tech Stack

- **Backend**: Node.js, Express  
- **Speech Services**:  
  - Google Cloud Speech‑to‑Text  
  - Google Cloud Text‑to‑Speech  
- **AI Summarization**: OpenAI API  
- **Frontend**: Vanilla HTML/CSS/JavaScript

## 📥 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Mozaaaik/speech-summary-ai.git 
```
### 2. Install dependencies
```bash
npm install
```

# 3. Configure credentials

This project uses **Google Cloud Speech-to-Text**, **Google Cloud Text-to-Speech**, and **OpenAI**.  
Before running the project, you need to create your own API keys.  

---

## a) Google Cloud Service Account

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).  
2. **Create a new project** (or select an existing one).  
3. In the left menu, go to **APIs & Services → Enable APIs and Services**.  
4. Enable the following APIs:  
   - ✅ **Cloud Speech-to-Text API**  
   - ✅ **Cloud Text-to-Speech API**  
5. Go to **IAM & Admin → Service Accounts**.  
6. Create (or select) a service account for this project.  
7. Open the **Keys** tab → **Add Key → Create New Key → JSON**  
8. Download the JSON file.  
9. Rename the file to **`credentials.json`** and place it into the backend folder:
10. 


---

## b) Text Summarization (Cohere AI)

This project uses **Cohere AI** to summarize long text chunks.

The summarization process works as follows:

1. The server reads your input text from `input.txt`.
2. It also reads a `prompt.txt` that contains your custom summarization instructions.
3. It splits the text into sentences and chunks them into ~100-word parts.
4. The chunks are sent to **Cohere AI Chat API** using the `command-a-03-2025` model.
5. The API response is normalized and saved into `output.txt`.
6. Finally, it returns a JSON response with the summary.

---

### Cohere API Key setup

To use Cohere AI summarization, you need your own API key.

1. Go to [Cohere Dashboard](https://dashboard.cohere.com/) and create an account.
2. Generate an API key.
3. Add it to your `.env` file:

   ```dotenv
   COHERE_API_KEY=your_cohere_api_key_here
   ```
---

## 🌐 OpenAI API Setup (Optional)

If you also want to use **OpenAI GPT models** in other routes, you’ll need your own API key.

1. Go to [OpenAI Dashboard](https://platform.openai.com/account/api-keys)
2. Generate an API key.
3. Add it to your `.env` file:

```dotenv
OPENAI_API_KEY=your_openai_key_here
```
## 🔑 Example `.env` file

Here’s an example `.env` file combining all required keys:

```dotenv
# OpenAI API key (for optional GPT routes)
OPENAI_API_KEY=sk-xxxxxxx

# Cohere API key (for summarization)
COHERE_API_KEY=your_cohere_key_here

# Google Cloud credentials path
GOOGLE_APPLICATION_CREDENTIALS=./credentials.json

# Server Port
PORT=3000
```

## ▶️ How to Run

1. **Install dependencies:**

```bash
npm install
```
2. **Start the backend server:**

```bash
node app.js
```
2. **Open the frontend in your browser:**

```bash
http://localhost:3000
```
## 📡 API Endpoints

|    Routes    | Method | Description                          |
|  ----------  | ------ | ------------------------------------ |
| `speech.js`  | POST   | Converts uploaded audio → raw text   |
| `summary.js` | GET    | Summarizes `input.txt` using Cohere  |
| `tts.js`     | POST   | Converts summary text → audio (MP3)  |

---

## ⚠️ Notes

- Do **NOT** commit your `.env` or `credentials.json` to GitHub.  
- API keys have usage limits. Check [Google Cloud Console](https://console.cloud.google.com/) and Cohere Dashboard for quotas.  
- If you deploy this project, make sure to securely store credentials (e.g., using Docker secrets or GitHub Actions secrets).  






   


