# Step-by-Step Guide to Create a Docker Image for a C Program

## Prerequisites
Before you begin, ensure that the following are installed on your machine:
- Docker: [Download and Install Docker](https://www.docker.com/get-started)
- A C compiler (e.g., GCC)
- A C program file (e.g., `main.c`)

## Steps to Create a Docker Image for a C Program

- Step 1: Write Your C Program
Create a simple C program, for example, `main.c`:

```
#include <stdio.h>

int main() {
    printf("Hello, Docker!\n");
    return 0;
}
```
- Step 2: Create a Dockerfile
The Dockerfile will contain instructions to build your Docker image. In the same directory as your main.c file, create a file named Dockerfile (without any file extension) and add the following content:

```
# Step 1: Use a base image with GCC installed (Ubuntu image in this case)
FROM ubuntu:20.04

# Step 2: Set the environment variable to avoid interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

# Step 3: Update package list and install build-essential (which includes gcc, make, etc.)
RUN apt-get update && apt-get install -y \
    build-essential \
    && apt-get clean

# Step 4: Set the working directory inside the container
WORKDIR /app

# Step 5: Copy the current directory (including demo.c) into the container
COPY . /app

# Step 6: Compile the demo.c program
RUN gcc demo.c -o demo

# Step 7: Define the command to run the compiled C program
CMD ["./demo"]


```
- Step 3: Build the Docker Image
In the terminal, navigate to the direvikas83pal/fun-factsctory where the Dockerfile and main.c file are located. Run the following command to build your Docker image:
```
docker build -t <image name> .

```

This command tells Docker to build an image from the current directory (.) and tag it with the name my-c-program.

- Step 4: Verify the Image Creation
Once the build completes, you can verify that the image was created by running:
```
docker images
```
- Step 5: run the docker image

```
sudo docker run <image name>

```
You should see the my-c-program image listed in the output.
