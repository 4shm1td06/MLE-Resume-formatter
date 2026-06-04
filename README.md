# MLE Resume Formatter

A recruiter-facing resume formatter that:
- uploads PDF or DOCX resumes
- extracts and structures content into an MLE-style schema
- lets users edit the parsed data
- exports the result as PDF or DOCX

## What's improved
- stronger MLE-style layout and preview
- broader recruiter fields like total experience, notice period, CTC, current designation, current company, highest qualification
- domain experience, tools/platforms, key achievements, projects, languages known, and additional sections
- DOCX generation support
- corrected OpenRouter environment usage and health check
- corrected upload/generated folder handling
- cleaner server-side normalization for all new fields

## Setup

### 1) Install
```bash
npm run install:all
```

If Puppeteer download is blocked in your environment:
```bash
PUPPETEER_SKIP_DOWNLOAD=1 npm run install:all
```

### 2) Configure server env
Create `server/.env` with:
```env
PORT=5050
OPENROUTER_API_KEY=your_key_here
OPENROUTER_SITE_URL=http://localhost:5050
OPENROUTER_APP_NAME=MLE Resume Formatter
# Optional if chrome/chromium is not auto-detected
# PUPPETEER_EXECUTABLE_PATH=/path/to/chrome
```

### 3) Run
```bash
npm run dev
```

## Endpoints
- `POST /api/resumes/parse`
- `POST /api/resumes/generate-pdf`
- `POST /api/resumes/generate-docx`
- `GET /api/health`

## Notes
- If `OPENROUTER_API_KEY` is missing or rate-limited, the app falls back to the heuristic parser.
- PDF export needs a working Chrome/Chromium runtime for Puppeteer.
- DOCX export uses the `docx` package and is available directly from the UI.
