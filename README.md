# auth-backend

FastAPI + PostgreSQL backend for the Auth App.

## Setup

```bash
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt

cp .env.example .env          # then edit .env with your DB credentials
uvicorn main:app --reload
```

## Environment Variables (`.env`)

```env
DATABASE_URL=postgresql://postgres:password@localhost:5432/authdb
SECRET_KEY=your-secret-key    # generate: openssl rand -hex 32
ACCESS_TOKEN_EXPIRE_MINUTES=60
```

## API Docs

Visit http://localhost:8000/docs after starting the server.

## Deploy to Railway / Render / Fly.io

Set the environment variables above in your hosting dashboard, then deploy this folder directly.

### Docker

```bash
docker build -t auth-backend .
docker run -p 8000:8000 --env-file .env auth-backend
```

## Endpoints

| Method | Endpoint            | Auth | Description       |
|--------|---------------------|------|-------------------|
| POST   | /api/auth/register  | ❌   | Create account    |
| POST   | /api/auth/login     | ❌   | Login, get JWT    |
| GET    | /api/users/me       | ✅   | Get current user  |
| PUT    | /api/users/me       | ✅   | Update profile    |
| DELETE | /api/users/me       | ✅   | Delete account    |
