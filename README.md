# OpenWebUI with Ollama - Docker Setup

This repository provides a **Docker Compose** setup for running **OpenWebUI** with **Ollama** support, utilizing **NVIDIA GPU acceleration**.

## 📌 What is OpenWebUI?

[OpenWebUI](https://github.com/open-webui/open-webui) is a web-based user interface designed for AI model interaction, supporting **Ollama**, **Llama models**, and other AI backends.

## 🛠 Services

### 🤖 OpenWebUI (with Ollama)

- **Container Name:** `open-webui-local`
- **Image:** `ghcr.io/open-webui/open-webui:ollama`
- **Ports:** `3009:8080` → Accessible at **`http://localhost:3009`**
- **Runtime:** Uses **NVIDIA GPU acceleration**
- **Environment Variables:**
  - `NVIDIA_VISIBLE_DEVICES=all` → Enables GPU access
- **Volumes:**
  - `./ollama:/root/.ollama` → Stores **Ollama-related data**
  - `./open-webui:/app/backend/data` → Stores **OpenWebUI configurations and models**
- **Restart Policy:** `always` → Ensures the container remains running

---

## 📌 Getting Started

### 1️⃣ Prerequisites

- **Docker & Docker Compose** installed → [Install Guide](https://docs.docker.com/get-docker/)
- **NVIDIA Drivers** and **NVIDIA Container Toolkit** installed for GPU acceleration
  - Install: [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)
- **Git Installed** (recommended for cloning the repository)

---

### 2️⃣ Clone the Repository

```sh
git clone https://github.com/your_username/openwebui-docker.git
cd openwebui-docker
```

### 3️⃣ Start the OpenWebUI Container

Run the following command to start:

```sh
docker compose up -d
```

### 4️⃣ Access the Web Interface

🌐 Open your browser and visit:  
**`http://localhost:3009`**

## ✨ Useful Commands

- **Check logs and container status:**

```sh
docker logs open-webui-local
```

- **Restart the container:**

```sh
docker compose restart
```

**Stop and remove the container:**

```sh
docker compose down
```

## ⚠️ Important Notes

1.  **GPU Acceleration**

    - Ensure you have **NVIDIA drivers** and the **NVIDIA Container Toolkit** installed.
    - The `NVIDIA_VISIBLE_DEVICES=all` environment variable allows access to all GPUs.

2.  **Data Persistence**

    - OpenWebUI stores models and configurations in `./open-webui`.
    - Ollama-related files are persistently stored in `./ollama`.

3.  **Port Configuration**

    - OpenWebUI runs internally on port **8080**, but is exposed as **3009** on the host.
    - Modify `docker-compose.yml` if you prefer a different port.

## 🚀 **Pro Tip:**

- Install custom AI models in OpenWebUI to maximize AI-powered workflows!
- Pair with Tailscale to get your own AI chat on the fly
