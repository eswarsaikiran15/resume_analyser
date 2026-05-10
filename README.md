# AI Resume Analyser 📄

**Live Preview:**  https://your-resume-analyser.streamlit.app/

An AI-powered tool that compares a resume against a job description and gives:
- Match score out of 10
- Matched and missing skills
- Resume improvement tips
- Likely interview questions
- PDF & CSV export
- Analysis history & caching
- Rate limiting & input validation

Built with **Groq API** + **Streamlit** + **SQLite** — runs fully on your laptop, completely free.

🚀 *A fresher project by Kamparapu Eswar Sai Kiran*


<img width="1890" height="845" alt="image" src="https://github.com/user-attachments/assets/bd75ed5a-fdc9-4c1b-8579-3726de88fd97" />
<img width="388" height="762" alt="image" src="https://github.com/user-attachments/assets/9a008ab1-9d5b-404f-b70c-251d8100d15f" />
<img width="1893" height="734" alt="image" src="https://github.com/user-attachments/assets/b402e586-a67b-4dc4-8645-94c1176fa61c" />
<img width="1375" height="702" alt="image" src="https://github.com/user-attachments/assets/ed38c386-e5fd-4914-882a-1fed132f58df" />
<img width="1312" height="782" alt="image" src="https://github.com/user-attachments/assets/3172f776-1239-49c3-af85-5ccd525b7bd6" />
<img width="1382" height="566" alt="image" src="https://github.com/user-attachments/assets/25e8aa45-56c8-4990-96fe-92edeb290193" />
<img width="1326" height="780" alt="image" src="https://github.com/user-attachments/assets/033ed239-9caa-4706-8794-82f88097bedd" />

---

## 🔐 Security First

**Your API key is NEVER stored in code or visible in the dashboard!**
- Stored safely in `.env` file (local only)
- `.env` is in `.gitignore` and never uploaded to GitHub
- Only you have access to your key
- Setup instructions are in this README, not in the app

---

## Setup (5 minutes)

### Step 1 — Get your free Groq API key
1. Go to https://console.groq.com
2. Sign up (free, no credit card required)
3. Navigate to **API Keys** in the left sidebar
4. Click **Create API Key**
5. Copy the key (it will look like: `gsk_...`)

### Step 2 — Create `.env` file
Create a file named `.env` in the project folder with:
```
GROQ_API_KEY=gsk_your_actual_key_here_replace_this
ENABLE_LOGGING=False
LOG_FILE=resume_analyser.log
```

**DO NOT commit this file to GitHub!** It's in `.gitignore` for protection.

### Step 3 — Install dependencies
```bash
pip install -r requirements.txt
```

### Step 4 — Run the app
```bash
streamlit run app.py
```

The app opens in your browser automatically at `http://localhost:8501`

---

## How to use

1. **App loads automatically** — API key is already loaded from `.env`
2. **On the left**: Paste or upload your **Job Description** (PDF or text)
3. **On the right**: Paste or upload your **Resume** (PDF or text)
4. Click **🔍 Analyse Resume**
5. View your:
   - ✅ Match score (out of 10)
   - ✅ Matched skills (green)
   - ✅ Missing skills (red)
   - ✅ Resume improvement tips
   - ✅ Likely interview questions
6. **Download results** as CSV or PDF

---

## Features

### 🎯 Core Analysis
- AI-powered resume matching using Groq API
- Match score (1-10)
- Verdict (Strong/Good/Average/Weak Match)
- Skill gap analysis
- Interview questions prediction

### 📁 Data Management
- **Session Caching** — Don't re-analyze same input
- **Database Storage** — All analyses saved in SQLite
- **Analysis History** — View past analyses with scores
- **CSV Export** — Spreadsheet format
- **PDF Export** — Professional report format

### 🛡️ Security & Validation
- **API Key in .env** — Not in code, not on GitHub
- **Input Validation** — Min/max character checks
- **Rate Limiting** — 30 seconds between analyses
- **Error Recovery** — Auto-retry with exponential backoff
- **Logging** — Track all operations

### ⚙️ Customization
- **Model Selection** — Choose from multiple Groq models
- **Temperature Control** — Adjust AI creativity (0.0-1.0)
- **Max Tokens** — Control response length
- **Dark Mode** — Professional dark theme

### 📊 Example Data
- Click **"📌 Load Example JD"** to see sample job description
- Click **"📌 Load Example Resume"** to see sample resume
- Perfect for testing before using real data

---

## What this project shows (for interviews)

- Python programming (APIs, databases, file handling)
- Security best practices (.env, .gitignore)
- Building a real UI with Streamlit
- Working with external APIs (Groq/LLM)
- Database design and queries (SQLite)
- Error handling & retry logic
- PDF/CSV generation
- Prompt engineering
- Rate limiting & caching
- Input validation
- Logging & debugging
- Practical problem solving

---

## Tech stack

| Component | Purpose |
|-----------|---------|
| Python 3.8+ | Core language |
| Streamlit | Web UI framework |
| Groq API | AI model (Llama, Mixtral, etc.) |
| SQLite | Data storage |
| PyPDF2 | PDF reading |
| ReportLab | PDF generation |
| python-dotenv | Environment variables |

---

## Project Structure

```
resume_analyser/
├── app.py                 # Main Streamlit app
├── requirements.txt       # Python dependencies
├── .env                   # Your API key (LOCAL ONLY, not on GitHub)
├── .env.example          # Template for .env file
├── .gitignore            # Prevents .env from being committed
├── resume_analyses.db    # Local database (created auto)
├── README.md             # This file
└── resume_analyser.log   # Activity log (if enabled)
```

---

## Sample Interview Answer

*"I built an AI Resume Analyser using Python, Streamlit, and the Groq API. It analyzes how well a resume matches a job description, providing a score, skill gaps, and interview questions. Key features include PDF upload, SQLite database storage, caching, rate limiting, and secure API key management using environment variables. The results can be exported as PDF or CSV. It demonstrates security best practices, database design, error handling, and practical AI integration."*

---

## Troubleshooting

### "API Key Not Found!"
- Create a `.env` file in the project folder
- Add: `GROQ_API_KEY=gsk_your_key_here`
- Make sure `.env` is in the same folder as `app.py`
- Reload the app

### "Model Decommissioned"
- Select a different model from the dropdown in sidebar
- Current active models:
  - `llama-3.1-8b-instant` ⚡ (Fastest)
  - `llama-3.3-70b-versatile` 🧠 (Most powerful)
  - `openai/gpt-oss-20b` (Balanced)

### "Rate Limit Error"
- Wait 30 seconds before next analysis
- Check Groq console for API usage: https://console.groq.com

### "PDF Not Extracting"
- Ensure PDF is not scanned image (must be text-based PDF)
- Try copying text manually instead

---

## Security Checklist

- ✅ API key in `.env` file (local only)
- ✅ `.env` in `.gitignore` (never committed)
- ✅ `.env.example` provided as template
- ✅ No hardcoded secrets in code
- ✅ Input validation to prevent injection
- ✅ Rate limiting to prevent abuse
- ✅ Database stored locally
- ✅ Activity logging available

---

## Performance Stats

- **Analysis Time**: 2-3 seconds (depends on model)
- **Cache Hit**: <100ms (instant)
- **PDF Generation**: ~1 second
- **Supports**: Resumes & JDs up to 10,000 characters

---

## Future Improvements

- [ ] User accounts & cloud storage
- [ ] Resume scoring trends/analytics
- [ ] Skill gap learning path recommendations
- [ ] Interview prep Q&A mode
- [ ] Multi-language support
- [ ] Resume template suggestions
- [ ] Email reports
- [ ] Batch processing (multiple resumes)

---

## Author & License

Built as a portfolio project for learning and demonstration.

**Technologies**: Python · Streamlit · Groq API · SQLite · ReportLab

---

## Support

For issues or suggestions:
1. Check `.env` file is set up correctly
2. Verify API key is valid at https://console.groq.com
3. Try selecting a different model
4. Check logs in `resume_analyser.log`
5. Review GitHub issues
