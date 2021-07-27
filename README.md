# Getting Started

A sample blog implenting FastAPI with sample user authentication. 

## venv
`python -m venv env`
`pip install fastapi uvicorn sqlalchemy graphene graphene-sqlalchemy alembic psycopg2-binary black python-dotenv`

## Docker 
`docker-compose build`
`docker-compose up`

`docker-compose run app alembic revision --autogenerate -m "New Migration"`
`docker-compose run app alembic upgrade head`

## Setup

We need to connect pgAdmin to our db

### PgAdmin

5050: pgAdmin Area
See `.env` for credentials


## Tooling Explained

1. Uvicorn: Simple Server
2. 
3. Alembic: DB Migrator, foils with SQLAlchemy.
    -  To run migration `docker-compose run app alembic revision --autogenerate -m "New Migration"`
    - To push migration `docker-compose run app alembic upgrade head`
4. Celery/Flower: Celery to de-queue tasks and Flower for monitoring.