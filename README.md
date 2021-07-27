# Getting Started

A sample blog implenting FastAPI with sample user authentication. 

## Tooling Explained

1. Uvicorn: Simple Server
2. SQLAlchemy: ORM DB toolkit (Can use standard Python classes - requires `fastapi-sqlachemy`) 
3. Alembic: DB Migrator, foils with SQLAlchemy.
    -  To run migration `docker-compose run app alembic revision --autogenerate -m "New Migration"`
    - To push migration `docker-compose run app alembic upgrade head`
4. Celery/Flower: Celery to de-queue tasks and Flower for monitoring.

## venv
`python -m venv env`
`pip install fastapi uvicorn sqlalchemy graphene graphene-sqlalchemy alembic psycopg2-binary black python-dotenv`
`alembic init alembic`

## Docker 
`docker-compose build`
`docker-compose up`

Use these queries to run new migrations.
`docker-compose run app alembic revision --autogenerate -m "{migration details}"`
`docker-compose run app alembic upgrade head`

### PgAdmin

5050: pgAdmin Area
See `.env` for credentials

### Sample Query Options 

mutation CreateNewPost{
  createNewPost(title:"new title1", content:"new content") {
    ok
  }
}

query{
  allPosts{
    title
  }
}

query{
  postById(postId:2){
    id
  	title
    content
  }
}

mutation newuser{
  createNewUser(username:"test1", password:"test1") {
    ok
  }
}

mutation authenticateUser{
  authenticateUser(username:"test10", password:"test10") {
    ok
  }
}


eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoidGVzdDEiLCJleHAiOjE2MjU1OTIyMDB9.4EaNBwe3yjg9NjwcC5F5S0zFaAr_QiOSTTGXjJqFHdk

mutation CreateNewPost{
  createNewPost(title:"new title1", content:"new content", token: "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoidGVzdDIwIiwiZXhwIjoxNjI1Njc4MzA1fQ.bUxdKz1KWougGZw-vRLdBGZN87WloCg-6Rai-bCObAc") {
    result
  }
}