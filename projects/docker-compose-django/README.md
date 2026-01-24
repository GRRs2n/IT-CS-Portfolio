# Docker Compose Django Deployment

## Overview

This project demonstrates deploying a basic Django web application with a PostgreSQL database using Docker Compose. Provided with a starter repository containing a Dockerfile, requirements.txt and source files, I modified the Dockerfile to use Python 3.10 to avoid compatibility errors with Django. I then created a `docker-compose.yml` file that defines two services: a PostgreSQL database and a Django app based on the updated Dockerfile. After generating a new Django project with `django-admin startproject`, I brought up both containers and verified the application by loading the Django welcome page in the browser.

## What I Did

- Examined the provided Dockerfile and updated it to use a Python 3.10 base image, ensuring compatibility with recent versions of Django【81672168035308†L23-L31】.
- Wrote a `docker-compose.yml` file that defines:
  - A `db` service using the official `postgres` image with environment variables for the database name, user and password.
  - A `web` service built from the updated Dockerfile, linking it to the `db` service and exposing port 8000.
- Ran `docker-compose run web django-admin startproject compose_example .` to generate the Django project files and confirmed that `manage.py` was created.
- Started both services with `docker-compose up --build`, then visited `http://localhost:8000` to confirm that the Django welcome page was served【81672168035308†L31-L38】.
- Observed the container logs updating when refreshing the page and reviewed the `docker-compose up` output to verify proper connectivity.

## Concepts and Lessons Learned

- **Docker Compose** simplifies orchestration of multi-container applications by allowing services to be defined together in a single YAML file. It eliminates the need to start containers manually and ensures that dependencies (such as the database) are available before the application starts【81672168035308†L62-L76】.
- **Ports vs. expose**: The `expose` directive makes a container’s port available to other services on the same Docker network, whereas the `ports` directive publishes the container’s port to the host machine【81672168035308†L45-L60】. In this project I mapped port 8000 so the Django app could be accessed via the browser.
- **Troubleshooting** image compatibility: Updating the Python base image in the Dockerfile resolved version conflicts between Python and Django【81672168035308†L23-L31】.
- Docker Compose provided a repeatable way to bring up the entire stack and tear it down when testing changes, which improves developer productivity and reduces errors【81672168035308†L62-L78】.

## Next Steps

- Add a volume mount for the Django application code to enable hot reloading during development.
- Integrate environment variables using a `.env` file to avoid hard‑coding credentials.
- Expand the Compose setup to include a production‑ready web server (such as Gunicorn) and Nginx reverse proxy.
