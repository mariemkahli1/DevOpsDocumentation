# Docker

## 1. **What is Docker**:

Docker is a tool designed to simplify the creation, deployment, and execution of applications using containers. Containers allow developers to package an application with all its dependencies and run it in isolation from the rest of the system.

## 2. **Key Concepts**:

- **Image:** A Docker image is a read-only template used to create containers. It contains everything needed to run an application: code, runtime, libraries, environment variables, and more.
- **Container:** A container is a running instance of an image. It is lightweight and portable, running in isolation.
  Dockerfile: A text file that contains instructions for building a Docker image.
- **Registry:** A repository for storing and distributing Docker images. Docker Hub is a popular example of a public registry.
- **Docker Engine:** The core component of Docker, Docker Engine is a client-server application that includes a server (a long-running daemon process), a REST API for interacting with the daemon, and a command-line interface (CLI) client.

***

### **Initialize Docker inside an application**

              docker init

### **Watch the service/container of an application**
It watches build context for service and rebuild/refresh 
containers when files are updated .

                docker compose watch

##  3. **Docker Image**: 

### 3.1 **Build an image from a Dockerfile:**:

     docker build -t  image_name path_to_dockerfile

### 3.2 **List all local images:**:

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

***

##  4. **Docker Container**: 

### 4.1 **Run a new container from an image:**

        docker run container_name image_name

### 4.2 **Run a named container from an image:**

      docker run --name container_name image_name:tag

### 4.3 **List all running containers:**

         docker ps

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

*** 

##  5. **Docker Compose**: 

### 5.1 **Create and start containers defined in a docker-compose.yml file**:
This command reads the docker-compose.yml file and starts the defined services in the background. 

         docker compose up
### 5.2 **Stop and remove containers defined in a docker-compose.yml file**:
 This command stops & removes the containers, networks, and volumes defined in the docker-compose.yml file.

         docker compose down
### 5.3 **Build or rebuild services**:
This command builds or rebuilds the Docker images for the 
services defined in the docker compose.yml file.

          docker compose build 
### 5.4 **List containers for a specific Docker Compose project**:
This command lists the containers for the services defined 
in the docker-compose.yml file.

            docker compose ps
### 5.5 **View logs for services**:
This command displays the logs for the services defined in the docker-compose.yml file.

             docker compose logs
### 5.6 **Scale services to a specific number of containers**:
This command scales the services defined in the docker-compose.yml file to the specified number of containers.

          docker compose up -d --scale 
           service_name=number_of_containers
### 5.7 **Run a one-time command in a service**:
             docker compose run service_name command 
### 5.8 **List all volumes:**
 Docker Compose creates volumes for services. This 
command helps you see them.

             docker volume ls 
### 5.9 **Pause a service**:
This command pauses the specified service.

                docker  pause service_name

### 5.10 **Unpause a service**:
This command unpauses the specified service.

            docker  unpause service_name 
### 5.11 **View details of a service**:
   Provides detailed information about a specific service

           docker compose ps service_name 

## 6. **Dockerfile**

 A Dockerfile is a script that contains instructions for 
building a Docker image. It defines the base image, sets up 
environment variables, installs software, and configures 
the container for a specific application or service.

### 6.1 **FROM**
 Specifies the base image for the Docker image.

          FROM ubuntu:20.04
### 6.2 **WORKDIR**
 Sets the working directory for subsequent instructions.
  
           WORKDIR /path/to/directory
### 6.3 **COPY**
Copies files or directories from the build context to the 
container

             COPY . .
### 6.4 **RUN**
 Executes commands in the shell. 

              RUN apt-get update  apt-get install -y curl
### 6.5 **ENV**
 Sets environment variables in the image.

               ENV NODE_VERSION=14
### 6.6 **EXPOSE**
 Informs Docker that the container listens on specified network ports at runtime.

                    EXPOSE port
### 6.7 **CMD**
Provides default commands or parameters for an executing container.

           CMD ["executable","param1","param2"] 

             CMD executable param1 param2
### 6.8 **ENTRYPOINT**
 Configures a container that will run as an executable.
          
              ENTRYPOINT ["executable","param1","param2"]

              ENTRYPOINT executable param1 param2
### 6.9 **ARG**
Defines variables that users can pass at build-time to the 
builder with the docker build command.

                ARG VERSION=latest

### 6.10 **VOLUME**
 Creates a mount point for external volumes or other 
containers. 

               VOLUME /path/to/volume
### 6.11 **LABEL**
Adds metadata to an image in the form of key-value pairs.

                    LABEL key="value"
### 6.12 **USER**
 Specifies the username or UID to use when running the 
image.

                 USER app

### 6.13 **ADD**
Copies files or directories and can extract tarballs in the 
process.Similar to COPY, but with additional capabilities (e.g., 
extracting archives).
               ADD source_path destination_path
                
 **DockerFile Example**

             # Use an official Node.js runtime as a base image 
              FROM node:20-alpine 

               # Set the working directory to /app 
                 WORKDIR /app 

             # Copy package.json and package-lock.json to the working 
               directory 

                COPY package*.json ./ 

             # Install dependencies 
               RUN npm install 

             # Copy the current directory contents to the container 
              COPY . .

              # Expose port 8080 to the outside world  
               EXPOSE 8080
 
              # Define environment variable 
               ENV NODE_ENV=production  

              # Run app.js when the container launches 
                CMD node app.js
