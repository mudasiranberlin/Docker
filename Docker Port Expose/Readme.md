# Run Apache Web Server Inside an Ubuntu Docker Container on Amazon EC2

This project demonstrates how to:

* Create an Amazon EC2 instance
* Install Docker on the EC2 instance
* Run an Ubuntu Docker container
* Install Apache Web Server inside the container
* Host a simple HTML website using Apache

---

## Architecture

```text
User
  |
  | HTTP Request
  v
Amazon EC2 Instance
  |
  | Docker
  v
Ubuntu Container (techserver)
  |
  | Apache Web Server
  v
Website: Hello, welcome to my website!
```

---

## Step 1: Create an EC2 Instance

Create an EC2 instance with:

* **AMI:** Amazon Linux
* **Instance Type:** Any suitable instance type
* **Security Group:** Allow inbound traffic on:

  * **SSH (Port 22)**
  * **HTTP (Port 80)**

Connect to the EC2 instance using SSH.

---

## Step 2: Switch to the Root User

```bash
sudo su
```

---

## Step 3: Install Docker

Install Docker using the following command:

```bash
yum install docker -y
```

Start the Docker service:

```bash
service docker start
```

You can verify that Docker is running:

```bash
service docker status
```

---

## Step 4: Run an Ubuntu Docker Container

Run an Ubuntu container named `techserver`:

```bash
docker run -td --name techserver -p 80:80 ubuntu
```

### Command Explanation

* `docker run` → Creates and runs a container
* `-t` → Allocates a terminal
* `-d` → Runs the container in detached mode
* `--name techserver` → Gives the container the name `techserver`
* `-p 80:80` → Maps EC2 port `80` to container port `80`
* `ubuntu` → Uses the Ubuntu Docker image

---

## Step 5: Check the Container Port

```bash
docker port techserver
```

Expected output:

```text
80/tcp -> 0.0.0.0:80
```

---

## Step 6: Enter the Docker Container

Connect to the running container:

```bash
docker exec -it techserver /bin/bash
```

You are now inside the Ubuntu container.

---

## Step 7: Update Ubuntu Packages

Inside the container, update the package list:

```bash
apt-get update
```

---

## Step 8: Install Apache Web Server

Install Apache:

```bash
apt-get install apache2 -y
```

---

## Step 9: Go to the Web Root Directory

Apache serves website files from:

```bash
cd /var/www/html
```

---

## Step 10: Create the Website

Create an `index.html` file:

```bash
cat > index.html
```

Add the following HTML code:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Docker Website</title>
</head>
<body>
    <h1>Hello, welcome to my website!</h1>
</body>
</html>
```

Press:

```text
Ctrl + D
```

to save the file.

---

## Step 11: Start Apache

Start the Apache Web Server:

```bash
service apache2 start
```

You can verify Apache is running:

```bash
service apache2 status
```

---

## Step 12: Access the Website

Copy the **Public IPv4 Address** of your EC2 instance and open it in your web browser:

```text
http://EC2-PUBLIC-IP
```

Example:

```text
http://54.123.45.67
```

You should see:

```text
Hello, welcome to my website!
```

---

## Complete Command Summary

### On the EC2 Instance

```bash
sudo su

yum install docker -y

service docker start

docker run -td --name techserver -p 80:80 ubuntu

docker port techserver

docker exec -it techserver /bin/bash
```

### Inside the Ubuntu Container

```bash
apt-get update

apt-get install apache2 -y

cd /var/www/html

cat > index.html
```

Add:

```html
<h1>Hello, welcome to my website!</h1>
```

Press `Ctrl + D` to save.

Then start Apache:

```bash
service apache2 start
```

---

## Important Note

Make sure your EC2 **Security Group allows inbound HTTP traffic on port 80**. Otherwise, you will not be able to access the website from your browser.

---

## Technologies Used

* Amazon EC2
* Docker
* Ubuntu
* Apache Web Server
* HTML

Mudasir Ahmad @anberlin






create ec2 macine and then sudo su 

after that go inside the ec2 machine and write there 

yum install docker -y

service docker start
docker run -td --name techserver -p 80:80 ubuntu


docker port techserver

docker exec -it techserver /bin/bash

apt-get update

apt-get install apache2 -y

cd /var/www/html

cat > index.html

<h1>Hello welocme to my website </h1>

service apache2 start
