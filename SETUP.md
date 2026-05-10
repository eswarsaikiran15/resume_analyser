# 🔐 Security & Setup Guide

## Quick Start (5 minutes)

### 1. Create `.env` File

In the project folder (`d:\resume_analyser`), create a new file named `.env`:

```
GROQ_API_KEY=gsk_your_actual_key_here
ENABLE_LOGGING=False
LOG_FILE=resume_analyser.log
```

**Replace `gsk_your_actual_key_here` with your real API key!**

### 2. Get Your API Key

1. Go to https://console.groq.com
2. Sign up (free, no credit card)
3. Click **API Keys** in the left sidebar
4. Click **Create API Key**
5. Copy the key (starts with `gsk_`)
6. Paste it in your `.env` file

### 3. Install Packages

```powershell
pip install -r requirements.txt
```

### 4. Run the App

```powershell
streamlit run app.py
```

---

## 🛡️ Security Details

### What's Protected?

✅ **API Key** — Stored in `.env` file (local only)
✅ **Database** — Stored locally (not uploaded)
✅ **Logs** — Stored locally (optional)
✅ **History** — Local SQLite database

### What's NEVER Stored Online?

❌ API keys
❌ User data
❌ Resume content
❌ Job descriptions
❌ Database files

---

## 📁 File Structure

```
resume_analyser/
│
├── app.py                    # Main application
├── requirements.txt          # Python packages
├── README.md                 # Documentation
├── SETUP.md                  # This file
│
├── .env                      # YOUR API KEY (DO NOT COMMIT!)
├── .env.example              # Template (safe to commit)
├── .gitignore               # Prevents .env upload
│
├── resume_analyses.db       # Created automatically
└── resume_analyser.log      # Created if logging enabled
```

---

## ❌ NEVER Do This

🔴 **Don't** add `.env` to GitHub
🔴 **Don't** paste API key in code
🔴 **Don't** share `.env` file
🔴 **Don't** commit database files
🔴 **Don't** push logs to GitHub

---

## ✅ Always Do This

✅ **Keep** `.env` file local only
✅ **Use** `.env.example` as template
✅ **Check** `.gitignore` includes `.env`
✅ **Rotate** API keys if leaked
✅ **Update** `.env` when key changes

---

## Environment Variables Explained

| Variable | Purpose | Required | Example |
|----------|---------|----------|---------|
| `GROQ_API_KEY` | Your API key | **YES** | `gsk_abc123...xyz` |
| `ENABLE_LOGGING` | Enable activity logs | Optional | `True` or `False` |
| `LOG_FILE` | Log file name | Optional | `resume_analyser.log` |

---

## Features

### ✅ Implemented Security Features

1. **API Key Management**
   - Loaded from `.env` file
   - Never exposed in UI
   - Not logged or stored

2. **Database Storage**
   - SQLite (local only)
   - No cloud upload
   - Full control over data

3. **Input Validation**
   - Min/max character checks
   - Prevents injection attacks
   - Validates file types

4. **Rate Limiting**
   - 30 seconds between analyses
   - Prevents API abuse
   - User-friendly messages

5. **Error Recovery**
   - Automatic retries (3x)
   - Exponential backoff
   - Clear error messages

6. **Logging & Audit**
   - Optional activity logging
   - Tracks analysis history
   - Database timestamps

---

## Troubleshooting

### Error: "API Key Not Found!"

**Solution:**
1. Check `.env` file exists in project folder
2. Verify `GROQ_API_KEY=gsk_...` is correct format
3. Reload the app (F5)

### Error: "GROQ_API_KEY=gsk_your_api_key_here_replace_with_actual_key"

**Solution:**
1. Replace the example text with your REAL key
2. Get key from https://console.groq.com
3. Save `.env` file
4. Reload app

### "Model Decommissioned"

**Solution:**
- Select different model from sidebar dropdown
- Current models are production-grade (always available)

### ".env file not recognized"

**Solution:**
1. Make sure file is named exactly `.env` (no `.txt`)
2. Place in project root folder
3. Reload terminal/app
4. Verify with: `cat .env`

---

## Best Practices

### Local Development

```bash
# Create .env from template
cp .env.example .env

# Edit .env with your key
nano .env

# Run app
streamlit run app.py
```

### Before Uploading to GitHub

1. Check `.gitignore` includes:
   ```
   .env
   .env.local
   *.db
   *.log
   ```

2. Verify `.env` is NOT in staging:
   ```bash
   git status  # Should NOT show .env
   ```

3. Only commit these:
   ```
   ✅ app.py
   ✅ requirements.txt
   ✅ .env.example
   ✅ .gitignore
   ✅ README.md
   ```

### Sharing Your Code

**Safe to share:**
- `app.py` — No secrets here
- `requirements.txt` — Just packages
- `README.md` — Documentation
- `.env.example` — Template without keys

**Never share:**
- `.env` — Your actual key
- `resume_analyses.db` — User data
- `*.log` — Activity logs

---

## API Key Rotation

If your API key is compromised:

1. Go to https://console.groq.com
2. Click API Keys
3. Delete old key
4. Create new key
5. Update `.env` file:
   ```
   GROQ_API_KEY=gsk_new_key_here
   ```
6. Reload the app

---

## Frequently Asked Questions

**Q: Is my resume stored on Groq servers?**
A: No. Your data stays local. Only the analysis request is sent to Groq.

**Q: Can someone steal my API key from GitHub?**
A: No. It's in `.env` which is in `.gitignore` and never uploaded.

**Q: What if I accidentally commit `.env`?**
A: 1) Delete the file from Git history, 2) Rotate your API key

**Q: Can I use the same key for multiple apps?**
A: Yes, but not recommended for security.

**Q: How long are analyses stored?**
A: Indefinitely in local database. Delete `resume_analyses.db` to clear.

---

## Support & Security Reports

- 🐛 **Bug Report**: Check README.md troubleshooting section
- 🔐 **Security Issue**: Delete `.env` immediately and create new key
- 📧 **Questions**: Review this guide or README.md

---

## Summary

| Task | Status | Command |
|------|--------|---------|
| Create .env | ⏳ TODO | Create file, add key |
| Install packages | ✅ DONE | Already installed |
| Get API key | ⏳ TODO | Visit console.groq.com |
| Run app | ⏳ TODO | `streamlit run app.py` |
| Use app | ⏳ TODO | Upload resume & JD |
| Deploy | ⏳ TODO | Use proper .env management |

---

**You're now secure and ready to go! 🚀**
