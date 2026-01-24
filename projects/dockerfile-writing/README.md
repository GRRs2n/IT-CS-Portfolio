# Dockerfile Writing and Best Practices

## Overview

This project demonstrates how to write a simple Dockerfile to package a Python application, then lint and test the container image.  The assignment involved creating a Dockerfile, building a container image, using **Hadolint** to check the file for best‑practice violations, and validating that the resulting image could run the application’s test suite.  These steps show familiarity with containerization basics and quality controls.

## What I did

- **Created a Dockerfile.** Wrote a Dockerfile that pulls a minimal Python base image, sets the working directory, copies the application source code and dependency list, installs dependencies with `pip install -r requirements.txt`, exposes the application port and declares the default command to start the app.  This exercise reinforces how to structure Dockerfiles logically.
- **Built a container image.** Ran `docker build -t myapp .` to build the image.  The build downloaded the base image layers, executed each Dockerfile instruction and produced a tagged image.
- **Linted with Hadolint.** Used the Hadolint tool to check the Dockerfile and received feedback on best practices (e.g., pinning versions, combining `RUN` commands).  Fixed warnings by simplifying layers and adding version pinning.  Linting ensures the image is secure and efficient【655286472738106†L7-L12】.
- **Ran the container.** Started the container with `docker run -p 5000:5000 myapp`.  Verified that the application responded correctly by sending HTTP requests and observing the expected output.
- **Tested the application.** Executed the project’s test suite inside the container to ensure the containerized application worked correctly.  This involved running `pytest` against the image or using curl commands to hit endpoints.  All tests passed, confirming the image was functional.

## Concepts & Lessons Learned

- **Layered build workflow.** Each line in a Dockerfile creates a new layer; reducing layers and leveraging caching speeds up builds.
- **Minimize base image size.** Choosing a small base (e.g., `python:3.11-slim`) reduces the attack surface and improves download times.
- **Use Hadolint.** Automated linting catches anti‑patterns and security issues early, prompting improvements before images are deployed【655286472738106†L7-L12】.
- **Expose vs. run ports.** `EXPOSE` documents which port the container listens on, but actual port mapping happens when running `docker run -p host:container`.  Documenting ports helps maintainers and orchestration tools.
- **Repeatable builds and tests.** Building, linting and testing within a container ensures a consistent environment across development, CI and production.

## Next Steps

- Convert the Dockerfile to a multi‑stage build to separate dependency installation from runtime, further reducing image size.
- Automate linting and testing using a CI pipeline (e.g., GitHub Actions) to enforce Dockerfile best practices on every commit.
- Publish the image to a registry and reference it from a Compose or Kubernetes deployment.
- Explore using non‑root users and proper file permissions within the container to improve security.

