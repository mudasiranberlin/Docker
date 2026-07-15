# Docker Volume Sharing Example

This project demonstrates how to create a Docker image with a volume and share that volume between two containers using the `--volumes-from` option.

## Prerequisites

- Linux system with Docker support
- Root or sudo privileges

## Step 1: Install Docker

```bash
yum install docker -y
```

Start the Docker service:

```bash
service docker start
```

## Step 2: Create a Dockerfile

Create a file named `Dockerfile`:

```bash
vi Dockerfile
```

Add the following content:

```dockerfile
FROM ubuntu

VOLUME ["myvolume"]
```

Save and exit the file.

## Step 3: Build the Docker Image

Build the image and tag it as `myimage`:

```bash
docker build -t myimage .
```

Verify the image:

```bash
docker images
```

## Step 4: Create the First Container

Run a container from the image:

```bash
docker run -it --name container1 myimage /bin/bash
```

Inside the container:

```bash
cd myvolume
touch myfile
exit
```

This creates a file named `myfile` inside the Docker volume.

## Step 5: Verify Images

```bash
docker images
```

## Step 6: Create a Second Container Sharing the Volume

Run another Ubuntu container that uses the volume from `container1`:

```bash
docker run -it --name container2 --privileged=true --volumes-from container1 ubuntu /bin/bash
```

Inside `container2`, verify the shared volume:

```bash
cd /myvolume
ls
```

Expected output:

```
myfile
```

This confirms that both containers are accessing the same Docker volume.

## Docker Commands Used

| Command | Description |
|---------|-------------|
| `docker build -t myimage .` | Builds the Docker image. |
| `docker images` | Lists available Docker images. |
| `docker run -it --name container1 myimage /bin/bash` | Creates the first container. |
| `docker run --volumes-from container1` | Shares volumes from an existing container. |
| `touch myfile` | Creates a file inside the shared volume. |

## Project Structure

```
.
├── Dockerfile
└── README.md
```

## Outcome

- Created a custom Ubuntu Docker image.
- Defined a Docker volume using the `VOLUME` instruction.
- Created a file inside the shared volume.
- Shared the volume between two containers using `--volumes-from`.
- Verified that data persisted across containers.
