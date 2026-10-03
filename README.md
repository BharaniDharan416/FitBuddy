# FitBuddy – AI Fitness Plan Generator

Complete implementation of the supplied FitBuddy specification: FastAPI backend, Jinja2 frontend, SQLite/SQLAlchemy persistence, Gemini AI integration, feedback-based plan updates, nutrition/recovery tips, admin dashboard, REST APIs, demo mode, and automated tests.

## Requirements
Python 3.11+ and a Gemini API key for live AI mode.

## Windows VS Code setup
```powershell
cd FitBuddy
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
Copy-Item .env.example .env
```
Edit `.env`. For initial testing leave `DEMO_MODE=true`. For live Gemini use `DEMO_MODE=false` and set `GEMINI_API_KEY`.

## Run
```powershell
uvicorn app.main:app --reload
```
Open http://127.0.0.1:8000 and API docs at http://127.0.0.1:8000/docs.

## Test
```powershell
pytest -q
```
Tests run in demo mode and do not need a Gemini key.

## API examples
`POST /api/workout`
```json
{"name":"Alex","user_id":"A001","age":19,"weight":70,"goal":"muscle gain","intensity":"medium"}
```
`POST /api/feedback`
```json
{"user_id":"A001","feedback":"Add more cardio and another recovery day."}
```

## Configuration
`.env` supports `GEMINI_PRO_MODEL` and `GEMINI_FLASH_MODEL`. This keeps the source specification's Pro/Flash responsibilities while allowing current Gemini model endpoints to be selected without changing Python code.

## Notes
The original document specifies Gemini 1.5 Pro and Gemini Flash. This implementation uses the current Google GenAI SDK and configurable model names instead of hard-coding an older SDK/model. The app has a safe demo mode so the entire UI/database/API flow can be tested without an API key.

FitBuddy is a general wellness demo, not medical diagnosis or treatment.
