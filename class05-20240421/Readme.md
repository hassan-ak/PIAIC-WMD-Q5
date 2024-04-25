# Getting Started with Docker

# Install Docker on Windows

1. Turn windows features on and off
   - Windows Subsystem for linux
   - Virtual machine platform
2. Open windows power shell as administrator
   - wsl --list --online
   - wsl --install -d Ubuntu-22.04
3. Install Docker Desktop
4. Update wsl to wsl 2 https://learn.microsoft.com/en-us/windows/wsl/install-manual
   - wsl --set-default-version 2
   - wal --set-version Ubuntu-22.04 2
5. Verify installations
   ```bash
   docker -v
   docker version
   docker run hello-world
   ```

## Topics

1. Virtualization
2. Cloud Native
   - Scalability
   - Reliable Platform
   - Running Applications
3. GenAI is the dominant cloud workload
4. CN supports certain aspects of AI and ML but still lot of issues to be addressed

## Virtualization

1. To successfully run our FastAPI codebase, it is essential to have multiple layers in place. Each layer plays a crucial role, and the absence of any single layer will prevent the desired results from being achieved. These layers include:

   - Computational and memory resources: Adequate computational power and memory allocation are necessary for the smooth execution of the FastAPI codebase.
   - Operating system: A compatible operating system environment is required to support the execution of the FastAPI code.
   - Tools (e.g., Python and Poetry): Essential tools such as Python and Poetry must be installed and configured properly to facilitate the execution of the FastAPI codebase.
   - Codebase: The FastAPI codebase itself is a fundamental layer, comprising the actual source code that defines the functionality of the application.
   - Installation: Proper installation procedures, including the setup of dependencies and environment configurations, are necessary to prepare the system for executing the FastAPI codebase.
   - Execution: Finally, executing the FastAPI code involves running the necessary commands or scripts to launch the application and make it accessible for use.

   By ensuring all these layers are in place and properly configured, we can effectively run our FastAPI codebase and achieve the desired results.

2. We possess the ability to generate virtual environments on our primary machine. These environments stand as isolated entities, offering a segregated realm wherein we can install and oversee dependencies autonomously, free from impacting the overarching environment of the main machine.

3. While the virtual environments leverage the physical resources of the main machine, they maintain autonomy in all other software installations, operating independently from one another.

4. There can be a potential issue with creating virtual environments wherein we may inadvertently allocate more resources to the virtual machine than necessary or vice versa. Also been an issue with the OS licensing.

## Containerization

1. Containerization, akin to virtualization, operates atop the primary resources of the system, offering the flexibility of dynamically utilizing resources as needed.

2. Containerization also gives us the opportunity to eliminate the need of os kernel thus installing just the required part of the OS and using Containerization also presents the opportunity to circumvent the necessity of a complete OS kernel installation by only installing the essential components of the OS and leveraging the kernel from the host system. This concept is exemplified in Windows Subsystem for Linux (WSL).

3. Docker Hub is the designated registry for acquiring Docker images. Hence, we will utilize the base image of an operating system sourced from Docker Hub.

4. When working with Docker, it's essential to have a `Dockerfile`. Let's explore the structure of this file:

   ```dockerfile
   # Start with a base image
   FROM python:3.12

   # Set metadata for the image
   LABEL maintainer="Your Name <your.email@example.com>"
   LABEL description="A brief description of the purpose of this Docker image."

   # Install dependencies
   RUN pip install poetry

   # Set working directory
   WORKDIR /code

   # Copy application code into the container
   COPY . /code

   # Install dependencies
   RUN poetry install

   # Specify the command to run when the container starts
   CMD ["unicorn", "run", "main.app:app", "--reload"]
   ```


# Docker Commands
1. docker --version ===> check docker version
2. docker version ===> client and server details
3. docker images ===> list all docker images on the system
4. docker inspect cimage-name ===> inspect docker image
5. docker build -f Dockerfile.dev -t image-name
6. docker run -d --name dev-cont1 -p 8000:8000 testing-docker-s-02
7. docker logs dev-cont1
8. docker logs dev-cont1 -f
9. docker ps
10. docker container ls
11. docker ps -a
12. docker rm dev-cont1
13. docker run -it --rm my-dev-image /bin/bash -c "poetry run pytest"



