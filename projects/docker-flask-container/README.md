# Dockerized Flask Application

## Overview
This project demonstrates containerizing a simple Python Flask web application, building a Docker image, and publishing it to Docker Hub.

## What I Did
- Installed Docker on a Linux host using the package manager.
- Cloned a sample Flask app repository and tested it locally with `python3 app.py`.
- Wrote a `Dockerfile` to containerize the app.
- Built a Docker image named `cplhello` using `docker build -t cplhello .`.
- Ran the container locally to verify the app on port 5000.
- Created a Docker Hub account and repository.
- Tagged the local image with my Docker Hub repository name.
- Logged in to Docker Hub using `docker login`.
- Pushed the image to Docker Hub using `docker push`.
- Removed local images and containers, pulled the image from Docker Hub, and ran it again to confirm deployment.

## Lessons Learned
- Docker simplifies packaging and deployment of applications by bundling dependencies.
- Tagging images allows versioning and identification when pushing to registries.
- Pushing images to Docker Hub enables easy sharing and deployment across hosts.
- Checking container status with `docker ps` and verifying images with `docker images` ensures correct operation.

## Next Steps
- Add environment variable configuration to parameterize the app.
- Use multi-stage builds to reduce image size.
- Integrate a CI/CD pipeline to build and push images automatically.
