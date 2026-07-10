# 🐳 Docker Custom Image with Dockerfile

A beginner-friendly Docker project that demonstrates how to create a custom Docker image using a **Dockerfile**, build the image, run a container, and verify that a file created during the build process exists inside the container.

---

## 📖 Project Overview

In this project, you will learn how to:

- Create a Dockerfile
- Build a custom Docker image
- Run a Docker container from the image
- Verify the contents of the container
- Understand basic Docker commands

---

## 📁 Project Structure

```text
.
├── Dockerfile
└── README.md
```

---

## 📝 Dockerfile

```dockerfile
FROM ubuntu:latest

RUN echo "Welcome to Mudasir" > /tmp/testfile
```

### Explanation

### `FROM ubuntu:latest`

- Downloads the latest Ubuntu image from Docker Hub.
- Uses Ubuntu as the base operating system for the custom image.

### `RUN`

```dockerfile
RUN echo "Welcome to Mudasir" > /tmp/testfile
```

- Executes a command while building the image.
- Creates a file named **testfile** inside the `/tmp` directory.
- Writes the text:

```text
Welcome to Mudasir
```

into the file.

---

# 🚀 Prerequisites

Before starting, make sure Docker is installed.

Check Docker version:

```bash
docker --version
```

Example:

```text
Docker version 25.0.14, build 0bab007
```

---

# 🔨 Build the Docker Image

Build the image using the Dockerfile.

```bash
docker build -t myimg .
```

### Command Breakdown

| Command | Description |
|----------|-------------|
| `docker build` | Builds a Docker image |
| `-t myimg` | Names the image **myimg** |
| `.` | Uses the current directory as the build context |

Expected output:

```text
Successfully built <IMAGE_ID>
Successfully tagged myimg:latest
```

---

# 📦 View Docker Images

List all Docker images.

```bash
docker images
```

Example:

```text
REPOSITORY    TAG       IMAGE ID       SIZE
myimg         latest    e617e254cedd   100MB
ubuntu        latest    4aaf0b273f92   100MB
```

---

# 📋 View Containers

Display all containers (running and stopped).

```bash
docker ps -a
```

Example:

```text
CONTAINER ID   IMAGE
4d04ece06a97   updateimage
3cccc05b607e   ubuntu
```

> **Note:**  
> Use:

```bash
docker ps -a
```

**NOT**

```bash
docker ps - a
```

The second command is incorrect because of the extra space.

---

# ▶️ Run the Docker Container

Create and start a container from the custom image.

```bash
docker run -it --name google myimg /bin/bash
```

### Command Breakdown

| Option | Description |
|---------|-------------|
| `docker run` | Creates a new container |
| `-it` | Opens an interactive terminal |
| `--name google` | Names the container **google** |
| `myimg` | Image name |
| `/bin/bash` | Starts a Bash shell |

---

# 📂 Verify the File

Move to the `/tmp` directory.

```bash
cd /tmp
```

List files.

```bash
ls
```

Output:

```text
testfile
```

Display the file contents.

```bash
cat testfile
```

Output:

```text
Welcome to Mudasir
```

This confirms that the file was successfully created during the image build process.

---

# 📌 Commands Used

```bash
# Check Docker version
docker --version

# Build image
docker build -t myimg .

# List Docker images
docker images

# List all containers
docker ps -a

# Run the container
docker run -it --name google myimg /bin/bash

# Navigate to /tmp
cd /tmp

# List files
ls

# View file content
cat testfile
```

---

# 🧠 Workflow

```text
Dockerfile
      │
      ▼
docker build
      │
      ▼
Docker Image (myimg)
      │
      ▼
docker run
      │
      ▼
Docker Container
      │
      ▼
Check /tmp/testfile
```

---

# 📚 Concepts Covered

- Docker
- Dockerfile
- Base Images
- Image Layers
- Docker Build
- Docker Images
- Docker Containers
- Docker Run
- Docker Commands
- File Creation During Build

---

# 🎯 Expected Output

Running the following command:

```bash
cat /tmp/testfile
```

should display:

```text
Welcome to Mudasir
```

---

# 🎉 Conclusion

This project demonstrates the fundamentals of creating and running a custom Docker image. You learned how to:

- Create a Dockerfile
- Build a Docker image
- Run a container
- Verify files created during the build process
- Work with essential Docker commands

This is a great starting point for learning Docker and containerization.
