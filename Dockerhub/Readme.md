# AWS EC2 Docker Image Creation and Deployment Using Docker Hub

## Project Overview

This project demonstrates how to create a custom Docker image on an AWS EC2 instance, push it to Docker Hub, and deploy the same image on another EC2 instance.

The process includes:

1. Creating an AWS EC2 instance.
2. Installing Docker.
3. Creating and modifying an Ubuntu Docker container.
4. Installing Apache and creating files inside the container.
5. Committing the container into a Docker image.
6. Pushing the image to Docker Hub.
7. Creating another EC2 instance.
8. Pulling and running the custom Docker image.
9. Verifying installed software and files.

---

# Step 1: Create First EC2 Instance

Create an EC2 instance with the following configuration:

* **AMI:** Amazon Linux
* **Instance Type:** Any suitable instance type
* **Security Group:**

  * Allow SSH traffic (Port 22)
  * Allow HTTP traffic (Port 80)

Connect to the EC2 instance using SSH.

Switch to root user:

```bash
sudo su
```

---

# Step 2: Install Docker

Install Docker on the EC2 instance:

```bash
yum install docker -y
```

Start Docker service:

```bash
service docker start
```

Check Docker service status:

```bash
service docker status
```

---

# Step 3: Create Ubuntu Docker Container

Run an Ubuntu container:

```bash
docker run -it ubuntu /bin/bash
```

Now you are inside the Ubuntu container.

---

# Step 4: Create Files and Install Software Inside Container

Create files:

```bash
touch file file1 file2 file3 file4
```

Install Apache web server:

```bash
apt-get update
apt-get install apache2 -y
```

Exit from the container:

```bash
exit
```

---

# Step 5: Create Docker Image From Container

Check all containers:

```bash
docker ps -a
```

Example output:

```
CONTAINER ID   IMAGE     NAME
xxxxxxxx       ubuntu    dreamy_edison
```

Commit the container into a new Docker image:

```bash
docker commit dreamy_edison image1
```

### Explanation:

* `dreamy_edison` → Name of the existing Ubuntu container.
* `image1` → Name of the new Docker image.

Verify the image:

```bash
docker images
```

---

# Step 6: Push Image to Docker Hub

Login to Docker Hub:

```bash
docker login
```

Enter your Docker Hub username and password.

Tag the Docker image:

```bash
docker tag image1 anberlin/project1
```

Push the image:

```bash
docker push anberlin/project1
```

The custom Docker image is now available in Docker Hub.

---

# Step 7: Create Second EC2 Instance

Create another EC2 instance with:

* **AMI:** Amazon Linux
* **Instance Type:** Any suitable instance type
* **Security Group:**

  * Allow SSH traffic (Port 22)
  * Allow HTTP traffic (Port 80)

Connect to the second EC2 instance using SSH.

Switch to root user:

```bash
sudo su
```

---

# Step 8: Install Docker on Second EC2 Instance

Install Docker:

```bash
yum install docker -y
```

Start Docker:

```bash
service docker start
```

Verify Docker status:

```bash
service docker status
```

---

# Step 9: Pull Docker Image From Docker Hub

Download the image:

```bash
docker pull anberlin/project1
```

Check downloaded images:

```bash
docker images
```

---

# Step 10: Run Custom Docker Container

Create and start a container from the downloaded image:

```bash
docker run -it --name mycontainer anberlin/project1 /bin/bash
```

Now you are inside the container.

---

# Step 11: Verify Files and Software

Check the files created earlier:

```bash
ls
```

Expected output:

```
file
file1
file2
file3
file4
```

Check Apache installation:

```bash
apache2 -v
```

The Apache software and created files are available because they were saved inside the Docker image.

---

# Complete Workflow

```
First EC2 Instance
        |
        |
Install Docker
        |
        |
Create Ubuntu Container
        |
        |
Create Files + Install Apache
        |
        |
Commit Container
        |
        |
Create Docker Image
        |
        |
Push Image to Docker Hub
        |
        |
Second EC2 Instance
        |
        |
Install Docker
        |
        |
Pull Image From Docker Hub
        |
        |
Run Container
        |
        |
Verify Files and Software
```

---

# Technologies Used

* AWS EC2
* Amazon Linux
* Docker
* Docker Hub
* Ubuntu
* Apache Web Server

---

# Project Summary

This project shows how Docker images can be created, stored in Docker Hub, and reused on different servers. By using Docker containers, applications and their dependencies can be packaged together and deployed consistently across environments.

# Author

Mudasir Ahmad / @ Anberlin



# first create ec2 machine 
Create an EC2 instance with:

AMI: Amazon Linux

Instance Type: Any suitable instance type

Security Group: Allow inbound traffic on:

SSH (Port 22)
HTTP (Port 80)
Connect to the EC2 instance using SSH.


sudo su


Step 3: Install Docker
Install Docker using the following command:

yum install docker -y
Start the Docker service:

service docker start
You can verify that Docker is running:

service docker status


docker run -it ubuntu /bin/bash

now inside the contaner create files install software 

touch file file1 file2 file3 file4

apt-get install apache2 -y

exit 




docker ps -a

docker commit dreamy_edison image1

dreamy_edison  is the ubuntu image name 

image1 = is the image name you are giving

docker images

docker login
enter username and password 

docker tag image1 anberlin/project1

 docker push anberlin/project1


 now create another ec2 machine 

 AMI: Amazon Linux

Instance Type: Any suitable instance type

Security Group: Allow inbound traffic on:

SSH (Port 22)
HTTP (Port 80)
Connect to the EC2 instance using SSH.


sudo su


Step 3: Install Docker
Install Docker using the following command:

yum install docker -y
Start the Docker service:

service docker start
You can verify that Docker is running:

service docker status

docker pull anberlin/project1

docker images

docker run -it --name mycontainer anberlin/project1 /bin/bash

inside you can check your softare and also files here i will check my file using 

ls 





