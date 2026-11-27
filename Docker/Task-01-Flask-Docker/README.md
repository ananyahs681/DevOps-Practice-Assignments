# Docker Task 1 – Build and Run a Dockerized Flask Application

## Objective
Build and run a simple Python Flask application inside a Docker container and access it through a browser.

## Technologies Used
- Python 3.9
- Flask
- Docker
- Docker Desktop

## Project Structure
```text
Task-01-Flask-Docker/
├── app.py
├── Dockerfile
├── README.md
└── screenshots/
```

## Application
The Flask application exposes a homepage at `/` and returns:

`Welcome to Dockerized Flask Application!`

## Dockerfile
The Dockerfile uses `python:3.9-slim` as its base image, copies the application into `/app`, installs Flask, exposes port 5000 and starts the application.

## Build the Docker Image
```bash
docker build -t flask-welcome-app:v1 .
```

## Run the Container
```bash
docker run -d --name flask-welcome-container -p 5001:5000 flask-welcome-app:v1
```

## Port Mapping
| Host port | Container port |
|---|---|
| 5001 | 5000 |

Host port 5000 was already occupied by a macOS process, so host port 5001 was used.

## Verify the Container
```bash
docker ps
```

## Test the Application
```bash
curl http://localhost:5001
```

Expected response:
`Welcome to Dockerized Flask Application!`

Browser URL: http://localhost:5001

## Cleanup
```bash
docker stop flask-welcome-container
docker rm flask-welcome-container
```

## Result
Successfully built a Docker image for a Flask application, launched it in a container, mapped the container port to the host and verified the application response.

## Evidence
Refer to the screenshots directory for implementation and verification screenshots.
