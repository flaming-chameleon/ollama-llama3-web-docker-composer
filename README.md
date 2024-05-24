[![Watch the video](https://img.youtube.com/vi/pbOZE2KkNuw/maxresdefault.jpg)](https://youtu.be/pbOZE2KkNuw)
[Here is my Youtube video](https://youtu.be/pbOZE2KkNuw): https://youtu.be/pbOZE2KkNuw


# Ollama Docker Compose Setup

This repository contains the Docker Compose configuration for running Ollama with the Llama3 model and its web interface. This setup simplifies the deployment of a powerful language model on your local machine with GPU acceleration.

## Prerequisites

To use this Docker Compose setup, you will need:

- Docker installed on your system. [Download Docker](https://www.docker.com/products/docker-desktop)
- Docker Compose installed (comes with Docker Desktop for Windows and Mac).
- An NVIDIA GPU with the latest drivers installed.
- NVIDIA Docker Toolkit to allow Docker to utilize the GPU. [Installation Guide](https://github.com/NVIDIA/nvidia-docker)

## Components

The setup consists of two main services:

1. **Ollama**: The service running the Ollama LLM with the Llama3 model.
2. **Ollama WebUI**: A web interface that interacts with the Ollama service to provide a user-friendly environment for interacting with the model.

## Directory Structure

```plaintext
/
├── docker-compose.yml
└── README.md
```

## Configuration

- `ollama`: Runs on port `11434` and utilizes an NVIDIA GPU.
- `ollama-webui`: Runs on port `3000` for web access.
- Persistent volumes are used to store model data and web interface data to ensure data persistence across container restarts.

## Usage

### Starting the Services

To start the services, run the following command in the directory containing your `docker-compose.yml`:

```bash
docker-compose up -d
```

This command will download the necessary Docker images, create the defined volumes, and start the services in detached mode.

### Accessing the Web UI

Once the containers are up and running, you can access the Ollama Web UI by navigating to:

```
http://localhost:3000
```

This interface will allow you to interact with the Ollama model directly from your browser.

### Stopping the Services

To stop the running services, use the following command:

```bash
docker-compose down
```

### Managing Data

The services use Docker volumes named `ollama` and `webui-data` to store data persistently. This data remains intact even after the services are stopped. To remove the data along with the services, you can run:

```bash
docker-compose down -v
```

This command will remove the containers and their associated volumes.

## Troubleshooting

If you have problems with docker drivers run this on Ubuntu

```bash
sudo apt-get update && sudo apt-get install -y nvidia-docker2
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)\ncurl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -\ncurl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update && sudo apt-get install -y nvidia-docker2
sudo systemctl restart docker
```


If you encounter any issues related to GPU access, ensure that the NVIDIA Docker Toolkit is properly installed and configured. Also, check the Docker and NVIDIA driver compatibility.

## Support

For support, feature requests, or bug reports, please open an issue in the repository or reach out via the [Ollama Community](https://ollama.ai/community).
