# KuzRAG

# Kotaemon Deployment Tutorial with Ollama and KuzAI (All-in-One) Full Local Stack.

## 1. Project Overview

Kotaemon (github.com/Cinnamon/kotaemon) is a Gradio-based web interface that leverages a local Ollama language model (LLM) 
that you can configure with KuzAI toolkit (github.com/Kusanagi8200/KuzAI).
This setup allows running a powerful, autonomous conversational AI locally without relying on external cloud APIs.


**Architecture:**

- **Ollama**: Hosts and serves local LLM models via a REST API.
- **KuzAI**: Toolkit for training and creating Ollama-compatible models.
- **Kotaemon**: Dockerized frontend interacting with Ollama’s API, providing a UI and file upload management.

---

## 2. Prerequisites

- Linux server with root or sudo access.
- Docker & Docker Compose installed.
- Network access to the Ollama API server (e.g., `10.12.248.187`).
- Clone or download the Kotaemon repository from GitHub.

---

## 3. Install Ollama & Prepare Your Model

### a) Install Ollama

Follow official instructions (https://ollama.com/docs).

### b) Create a Custom Ollama Model Using KuzAI

- KuzAI repo: https://github.com/Kusanagi8200/KuzAI
- Train or build your `kuzrag-full` Ollama model using KuzAI.

### c) Run Ollama as a Local Server

```bash
sudo -u ollama env OLLAMA_HOST="0.0.0.0:11434" OLLAMA_MODELS=/usr/share/ollama/.ollama/models ollama serve &
```
This runs Ollama on all interfaces, port 11434, serving models located in the specified directory.

### Test the Ollama API

curl http://10.12.248.187:11434/v1/models

You should receive a JSON list of available models including kuzrag-full.


## 4. Install Docker & Setup Kotaemon
   
### a) Install Docker and Docker Compose

sudo apt update
sudo apt install docker.io docker-compose -y
sudo systemctl enable --now docker

### b) Create Project Structure

mkdir -p kotaemon/uploads
cd kotaemon

### c) Create Configuration Files
env.local
```
MODEL=ollama
MODEL_NAME=kuzrag-full:latest
BASE_URL=http://10.12.248.187:11434
API_KEY=dummy

OPENAI_API_KEY=false
AZURE_OPENAI_API_KEY=false
COHERE_API_KEY=false
GOOGLE_API_KEY=false

GRADIO_SERVER_NAME=0.0.0.0
GRADIO_SERVER_PORT=7860

KH_DEMO_MODE=false
KH_AUTH_TYPE=none
KH_LOG_LEVEL=INFO
KH_LOG_REQUESTS=true

USE_CUSTOMIZED_GRAPHRAG_SETTING=false
```

### d) Create docker-compose.yml
```
version: "3.8"

services:
  kuzrag:
    container_name: kuzrag
    image: ghcr.io/cinnamon/kotaemon:main-ollama
    restart: unless-stopped
    ports:
      - "7860:7860"
    env_file:
      - ./env.local
    volumes:
      - ./uploads:/app/uploads
```

## 5. Launch Kotaemon

docker compose up -d
docker ps  # Verify container is running

## 6. Access and Use

    Open your browser at http://<server_ip>:7860 (e.g., http://10.12.248.187:7860).

    Login with admin/admin.

    Upload files and interact with your local kuzrag-full Ollama model through the web UI.

______________________________________________________________________________________________________________________________ 

## 7. You have to configure your models in Kotaemon for default use 

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-Add-Model.png">
 <source media="(prefers-color-scheme: light)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-Add-Model.png">
 <img alt="" src="">
</picture>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-Connect-Model.png">
 <source media="(prefers-color-scheme: light)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-Connect-Model.png">
 <img alt="" src="">
</picture>

______________________________________________________________________________________________________________________________ 

## 8.Upload some file to Process 

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-Upload-Files.png">
 <source media="(prefers-color-scheme: light)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-Upload-Files.png">
 <img alt="" src="">
</picture> 

______________________________________________________________________________________________________________________________ 

## 9. Process Files 

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-Process-File.png">
 <source media="(prefers-color-scheme: light)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-Process-File.png">
 <img alt="" src="">
</picture> 

______________________________________________________________________________________________________________________________ 

## 10. Mind Mapp 

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-MindMap.png">
 <source media="(prefers-color-scheme: light)" srcset="https://github.com/Kusanagi8200/KuzRAG/blob/main/KuzRAG-MindMap.png">
 <img alt="" src="">
</picture> 

______________________________________________________________________________________________________________________________

## 11. Notes

    API_KEY=dummy disables API key enforcement, since Ollama local server doesn't require authentication.

    Uploaded files persist in the local uploads folder, mounted as a Docker volume.

    All external cloud APIs (OpenAI, Azure, Google, Cohere) are disabled for a fully local setup.


## Final Project Structure

kotaemon/ 

├── docker-compose.yml 

├── env.local 

└── uploads/ 

______________________________________________________________________________________________________________________________ 


## 11. Extra 

sudo -u ollama env OLLAMA_HOST="0.0.0.0:11434" OLLAMA_MODELS=/usr/share/ollama/.ollama/models ollama serve &

sudo -u ollama env OLLAMA_HOST=0.0.0.0:11434 OLLAMA_MODELS=/usr/share/ollama/.ollama/models ollama serve

curl http://10.12.248.187:11434/v1/models

docker run --rm -it   --name kuzrag   -e MODEL=ollama   -e MODEL_NAME=kuzrag-full:latest   -e BASE_URL=http://10.12.248.187:11434   -e API_KEY=dummy   -e EMBEDDING_MODEL_NAME=nomic-embed-text   -p 7860:7860   ghcr.io/cinnamon/kotaemon:main-ollama

______________________________________________________________________________________________________________________________
  
