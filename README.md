# FSE4AI 2025 - Dockerized Unix Environments

Welcome to the FSE4AI 2025 practicals\! This guide will help you get the necessary Unix environments running on your machine using Docker.

### \#\# What is Docker? 🐳

Docker is a tool that offers a way to package an application with everything it needs to run ( libraries, tools, and settings) into a box called a **container**. This container can run on any computer with Docker installed, providing a guarantee that the environment inside is always the same.

  * **Image**: A blueprint or a template for creating a container (e.g., `ubuntu-with-my-tools`).
  * **Container**: A running instance of an image. It's the actual "box" where your application lives.

This project provides pre-built Docker images for each practical, so you don't have to worry about complex setup.

-----

## Getting Started (One-Time Setup)

### **Prerequisites**

Before you begin, make sure you have these two tools installed:

1.  **Git**: To download the project files. (Install Git)
2.  **Docker Desktop**: The application that runs and manages containers. (Install Docker Desktop)

### **Step 1: Clone the Repository**

Open your terminal, navigate to where you want to store the project, and run this command to download the project files:

```sh
git clone https://github.com/skolai/fse4ai_2025.git
cd fse4ai_2025, or wherever it is located on your device
```

### **Step 2: Start Docker Desktop**

Launch the Docker Desktop application. You must have it running in the background for any Docker commands to work. You should see a small whale icon in your system tray or menu bar.

-----

## Running the Practicals

Here's how to run the container for each practical.

### **Practical 1: `01_local_unix`**

#### 1\. Pull the Image

This command downloads the pre-built image from the GitHub Container Registry.

```sh
docker pull ghcr.io/skolai/fse4ai_2025_01_local_unix:29.09.01
```

#### 2\. Run the Container

This command starts an interactive container from the image.

```sh
docker run --rm -it ghcr.io/skolai/fse4ai_2025_01_local_unix:29.09.01
```

  * `--rm`: Automatically deletes the container when you exit.
  * `-it`: Gives you an interactive terminal inside the container.

-----

### **Practical 2: `02_local_unix`**

#### 1\. Pull the Image

```sh
docker pull ghcr.io/skolai/fse4ai_2025_02_local_unix:01.10.01
```

#### 2\. Run the Container

```sh
docker run --rm -it ghcr.io/skolai/fse4ai_2025_02_local_unix:01.10.01
```

-----

### **Practical 3: `03_remote_unix` (Client/Server)**

This practical has two images: a server and a client. You'll likely run them in separate terminals.

#### 1\. Pull the Images

```sh
# Pull the server image
docker pull ghcr.io/skolai/fse4ai_2025_remote_unix-server:03.10.03

# Pull the client image
docker pull ghcr.io/skolai/fse4ai_2025_remote_unix-client:03.10.04
```

#### 2\. Run the Containers

You will need two terminals open.

  * **In Terminal 1 (Server):**
    ```sh
    docker compose up --build -d fse4ai_03_server fse4ai_03_client
    docker exec -it fse4ai-fse4ai_03_client-1 bash

    ```

-----
