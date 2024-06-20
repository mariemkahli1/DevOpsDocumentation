# Docker

## 1. **What is Docker**:

Docker is a tool designed to simplify the creation, deployment, and execution of applications using containers. Containers allow developers to package an application with all its dependencies and run it in isolation from the rest of the system.

## 2. **Key Concepts**:

- **Image:** A Docker image is a read-only template used to create containers. It contains everything needed to run an application: code, runtime, libraries, environment variables, and more.
- **Container:** A container is a running instance of an image. It is lightweight and portable, running in isolation.
  Dockerfile: A text file that contains instructions for building a Docker image.
- **Registry:** A repository for storing and distributing Docker images. Docker Hub is a popular example of a public registry.
- **Docker Engine:** The core component of Docker, Docker Engine is a client-server application that includes a server (a long-running daemon process), a REST API for interacting with the daemon, and a command-line interface (CLI) client.

## <mark> 3. **Docker Image**: </mark>

### 3.1 **Build an image from a Dockerfile:**:

     docker build -t  image_name path_to_dockerfile

### 3.2 ** List all local images:**:

      docker images

### 3.3 **Pull an image from Docker Hub:**

      docker pull image_name:tag

### 3.4 **Remove a local image:**

       docker rmi image_name:tag

### 3.5 **Tag an image**:

     docker tag source_image:tag new_image:tag

### 3.6 **Push an image to Docker Hub:**

     docker push image_name:tag

### 3.7 **Inspect details of an image:**

      docker image inspect image_name:tag

### 3.8 **Save an image to a tar archive**:

     docker save -o image_name.tar  image_name:tag

### 3.9 **Load an image from a tar archive:**

      docker load  -i  image_name.tar

### 3.10 **Prune unused images**:

          docker image  prune

## <mark> 4. **Docker Container**: </mark>

### 4.1 **Run a new container from an image:**

        docker run container_name image_name

### 4.2 **Run a named container from an image:**

      docker run --name container_name image_name:tag

### 4.3 **List all running containers:**

         dockerps

### 4.4 **List all containers (including stopped ones):**

       docker -a

### 4.5 **Stop a running container:**

       docker stop container_name_or_id

### 4.6 **Restart a stopped container:**

      docker start  container_name_or_id

### 4.7 **Run container in interactive mode:**

        docker run -it container_name_or_id

### 4.8 **Run container in interactive shell mode**:

      docker run -it container_name_or_id sh

### 4.9 **Remove a stopped container:**:

           dockerrm container_name_or_id

### 4.10 **Remove a running container (forcefully):**

       docker rm -f container_name_or_id

### 4.11 **Inspect details of a container:**

       docker inspect container_name_or_id

### 4.12 **View container logs**:

       docker logs container_name_or_id

### 4.13 **Pause a running container**:

         docker pause  container_name_or_id

### 4.14 **Unpause a paused container**:

         docker unpause  container_name_or_id

## <mark> 5. **Docker Compose**: </mark>
