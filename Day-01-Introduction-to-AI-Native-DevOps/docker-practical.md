# Docker Practical – AI-Native DevOps

## 1. Objective
Build, run, and test a containerized application using Docker
with assistance from Claude Code.

## 2. Prerequisites
- Docker installed and running
- Python installed
- Git installed
- Claude Code installed and configured

## 3. Create the Application
Create the Flask application with:
- `/` – Home endpoint
- `/health` – Health-check endpoint

## 4. Install Dependencies
pip install flask

## 5. Test the Application
Run the Flask application and verify the endpoints.

## 6. Build the Docker Image
docker build -t claude-devops-app:v1 .

## 7. Run the Docker Container
docker run -d --name claude-app -p 5000:5000 claude-devops-app:v1

## 8. Verify the Container
docker ps
docker logs claude-app
curl http://localhost:5000/
curl http://localhost:5000/health

## 9. Troubleshooting
If the application fails:
- Check container logs.
- Verify port mapping.
- Check the application bind address.
- Inspect configuration changes before rebuilding.

## 10. Git Version Control
git status
git add .
git commit -m "Add Docker practical"
git push origin main

## 11. Cleanup
docker stop claude-app
docker rm claude-app