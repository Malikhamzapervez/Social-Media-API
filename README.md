# FastAPI Social Media API

A social media backend built with **FastAPI** and **PostgreSQL**. The project provides authenticated users with APIs to create, manage, and vote on posts.

## Features

- User registration and user lookup
- OAuth2 password login with JWT access tokens
- Secure password hashing with `bcrypt`
- Create, read, update, and delete post operations
- Post search, pagination, and vote counts
- Vote and remove-vote functionality
- Request validation with Pydantic
- SQLAlchemy database models and dependency injection
- Database versioning with Alembic
- Interactive API documentation through Swagger UI

## Tech Stack

- Python
- FastAPI
- PostgreSQL
- SQLAlchemy
- Pydantic
- Alembic
- JWT (`python-jose`)
- bcrypt
- Uvicorn
- Postman

## Project Structure

```text
FastApi/
├── app/
│   ├── routes/          # Authentication, users, posts, and votes
│   ├── config.py        # Environment-based settings
│   ├── database.py      # PostgreSQL connection and sessions
│   ├── models.py        # SQLAlchemy models
│   ├── Schema.py        # Pydantic request and response schemas
│   └── main.py          # FastAPI application
├── alembic/
│   └── versions/        # Database migration history
├── postman/             # Postman API collection
├── requirements.txt
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.10+
- PostgreSQL

### 1. Clone the repository

```bash
git clone https://github.com/Malikhamzapervez/Social-Media-API.git
cd FastApi
```

### 2. Create and activate a virtual environment

Windows PowerShell:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

Create `app/.env`:

```env
DATABASE_HOSTNAME=localhost
DATABASE_PORT=5432
DATABASE_PASSWORD=your_postgres_password
DATABASE_NAME=social_media_app
DATABASE_USERNAME=postgres
SECRET_KEY=replace_with_a_secure_secret
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

Create the PostgreSQL database named `social_media_app` (or use the database name configured above).

### 5. Run database migrations

```bash
alembic upgrade head
```

### 6. Start the API

```bash
uvicorn app.main:app --reload
```

The API will be available at `http://127.0.0.1:8000`.

## API Documentation

Once the server is running:

- Swagger UI: `http://127.0.0.1:8000/docs`
- ReDoc: `http://127.0.0.1:8000/redoc`

## Main Endpoints

| Method | Endpoint | Description |
| --- | --- | --- |
| POST | `/users/` | Register a user |
| GET | `/users/{id}` | Get a user |
| POST | `/login` | Log in and receive a JWT |
| GET | `/posts` | List posts with search and pagination |
| POST | `/posts` | Create a post |
| GET | `/posts/{id}` | Get a post |
| PUT | `/posts/{id}` | Update a post |
| DELETE | `/posts/{id}` | Delete a post |
| POST | `/vote/` | Add or remove a vote |

Most post and vote endpoints require a bearer token. After logging in, authorize requests in Swagger UI using:

```text
Authorization: Bearer <access_token>
```

## Database Migrations

Create a new migration after changing the SQLAlchemy models:

```bash
alembic revision --autogenerate -m "describe your change"
alembic upgrade head
```

## Learning Outcomes

This project was built to practice REST API design, authentication and authorization, password security, relational database modeling, schema validation, pagination, migrations, and clean route organization with FastAPI.

## License

This project is available for learning and portfolio purposes.
