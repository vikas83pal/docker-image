# Step-by-Step Guide to Create a Docker Image for a C Program

## Prerequisites
Before you begin, ensure that the following are installed on your machine:
- Docker: [Download and Install Docker](https://www.docker.com/get-started)
- A C compiler (e.g., GCC)
- A C program file (e.g., `main.c`)

## Steps to Create a Docker Image for a C Program

### Step 1: Write Your C Program
Create a simple C program, for example, `main.c`:

```c
#include <stdio.h>

int main() {
    printf("Hello, Docker!\n");
    return 0;
}

### Step 2: Create a Dockerfile
The Dockerfile will contain instructions to build your Docker image. In the same directory as your main.c file, create a file named Dockerfile (without any file extension) and add the following content:

```
# Step 1: Use an official GCC image as a base image
FROM gcc:latest

# Step 2: Set the working directory in the container
WORKDIR /usr/src/app

# Step 3: Copy the C program source file into the container
COPY main.c .

# Step 4: Compile the C program using GCC
RUN gcc -o myprogram main.c

# Step 5: Define the default command to run the compiled program
CMD ["./myprogram"]

```
### Step 3: Build the Docker Image
In the terminal, navigate to the direvikas83pal/fun-factsctory where the Dockerfile and main.c file are located. Run the following command to build your Docker image:
```
docker build -t <image name> .
```

This command tells Docker to build an image from the current directory (.) and tag it with the name my-c-program.

### Step 4: Verify the Image Creation
Once the build completes, you can verify that the image was created by running:
```
docker images
```
You should see the my-c-program image listed in the output.
