# Updates (Feb 15 2025, by Jake HYUN OH KWON)
List of items I had to do to make everything work.
1)Fork repo 
2)create and activate a virtual environment python3 -m venv env ; source env/bin/activate
3)add env on source code 
4)install package (pip install -r requirements.txt)
downloaded rust, cargo
adjusted python version to 3.11 
5)postgres setting 
brew services start postgresql@14
psql -U $(whoami) 
CREATE ROLE postgres WITH LOGIN SUPERUSER PASSWORD 'password'; CREATE DATABASE mydatabase WITH OWNER postgres;
alembic upgrade head
6)docker compose (docker compose up --build) 
7)run application (uvicorn src.main:app --host 0.0.0.0 --port 8000 --reload)
8)added .github > workflows > conventional-commit.yml
9)added .github > workflows > nightly-build.yml
1)added .github > workflows > release.yml 
            also added .releaserc.json
            also downloaded semantic release (pip install python-semantic-release)
            added tags ( git tag v1.0.0  ; git push origin v1.0.0 ) 
11)made dockerhub, ethereal account and added secrets 
12)test :
            commit and push
            make pull request (on github -> test runs and PR passes)
            Semantic release -> version update and creates Github Release 
            nightly build (on github -> action tab -> Run Workflow) 
                      added env info 
	            added pytest in requirement.txt  
            check if image was pushed to DockerHub (docker pull hkwon7/fastapi-beyond-crud:latest)
 






# FastAPI Beyond CRUD 

This is the source code for the [FastAPI Beyond CRUD](https://youtube.com/playlist?list=PLEt8Tae2spYnHy378vMlPH--87cfeh33P&si=rl-08ktaRjcm2aIQ) course. The course focuses on FastAPI development concepts that go beyond the basic CRUD operations.

For more details, visit the project's [website](https://jod35.github.io/fastapi-beyond-crud-docs/site/).

## Table of Contents

1. [Getting Started](#getting-started)
2. [Prerequisites](#prerequisites)
3. [Project Setup](#project-setup)
4. [Running the Application](#running-the-application)
5. [Running Tests](#running-tests)
6. [Contributing](#contributing)

## Getting Started
Follow the instructions below to set up and run your FastAPI project.

### Prerequisites
Ensure you have the following installed:

- Python >= 3.10
- PostgreSQL
- Redis

### Project Setup
1. Clone the project repository:
    ```bash
    git clone https://github.com/jod35/fastapi-beyond-CRUD.git
    ```
   
2. Navigate to the project directory:
    ```bash
    cd fastapi-beyond-CRUD/
    ```

3. Create and activate a virtual environment:
    ```bash
    python3 -m venv env
    source env/bin/activate
    ```

4. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

5. Set up environment variables by copying the example configuration:
    ```bash
    cp .env.example .env
    ```

6. Run database migrations to initialize the database schema:
    ```bash
    alembic upgrade head
    ```

7. Open a new terminal and ensure your virtual environment is active. Start the Celery worker (Linux/Unix shell):
    ```bash
    sh runworker.sh
    ```

## Running the Application
Start the application:

```bash
fastapi dev src/
```
Alternatively, you can run the application using Docker:
```bash
docker compose up -d
```
## Running Tests
Run the tests using this command
```bash
pytest
```

## Contributing
I welcome contributions to improve the documentation! You can contribute [here](https://github.com/jod35/fastapi-beyond-crud-docs).
