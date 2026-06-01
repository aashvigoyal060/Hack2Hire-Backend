# Hack2Hire Backend

Express API for the AI interview platform, deployed on Railway.

## Live URL

[https://hack2hire-backend-production.up.railway.app/health](https://hack2hire-backend-production.up.railway.app/health)

## Tech Stack

- Node.js + Express (ES modules)
- Drizzle ORM (PostgreSQL)
- Multer (file upload)
- pdf-parse (resume parsing)
- OpenAI API (for AI features)

## Features

- Resume ATS score & analysis
- AI interview questions & scoring
- Tech quiz generation
- LeetCode-style problem generation
- English & Math aptitude practice
- Session history
- Speech-to-text & text-to-speech integration (frontend handles most TTS/STT)

## Health Check

- `GET /health`
- `GET /api/health`

## API Endpoints

### Interviews

- `GET /api/interviews` - List all interviews
- `POST /api/interviews` - Create new interview
- `GET /api/interviews/:id` - Get interview details
- `POST /api/interviews/:id/next` - Next question
- `POST /api/interviews/:id/complete` - Complete interview

### Practice

- `POST /api/practice/quiz` - Tech quiz (skills, optional count, job description)
- `POST /api/practice/leetcode` - LeetCode problems (skills, count, difficulty, job description)
- `POST /api/practice/english` - English aptitude quiz
- `POST /api/practice/math` - Math aptitude quiz

### Resume

- `POST /api/resume/analyze` - Analyze PDF resume (ATS score, keywords, etc.)

## Railway Setup

1. Connect repo: `aashvigoyal060/Hack2Hire-Backend`
2. Set Variables (required):

| Variable | Example |
|----------|---------|
| `DATABASE_URL` | `postgresql://user:password@neon.tech/neondb?sslmode=require` |
| `AI_INTEGRATIONS_OPENAI_API_KEY` | `sk-proj-...` |
| `AI_INTEGRATIONS_OPENAI_BASE_URL` | `https://api.openai.com/v1` |
| `CORS_ORIGIN` | `https://hack2-hire-woad.vercel.app` |

3. Railway sets `PORT` automatically; don't change it.
4. Redeploy to apply changes.

## Local Development

```bash
cp .env.example .env
# Edit .env with your variables
npm install
npm run db:push  # Push Drizzle schema to DB
npm run dev      # Dev server on http://localhost:5000
```

## Production Build

```bash
npm run build
npm start
```
