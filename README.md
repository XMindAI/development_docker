# Development Docker images
Deep learning development tools using Docker

[![Build Status](https://dev.azure.com/XMindAI/OpenXMind/_apis/build/status/XMindAI.development_docker?branchName=master)](https://dev.azure.com/XMindAI/OpenXMind/_build/latest?definitionId=6&branchName=master)

## Instructions

* Get docker (at least 19.03)
* Get nvidia-container-toolkit: https://github.com/NVIDIA/nvidia-docker


Add these lines to your .bashrc or .zshrc, this enables using docker with own user:
```bash
export GID=$(id -g)
export USER=$(id -u -n)
export HOST_GROUP=$(id -g -n)
export UID=${UID}
```

Set Nvidia as default container runtime for Docker in `/etc/docker/daemon.json`:
```
{
    "default-runtime": "nvidia",
    "runtimes": {
        "nvidia": {
            "path": "nvidia-container-runtime",
            "runtimeArgs": []
        }
    }
}
```


## Available Docker images
Supported CUDA versions: `10.0`, `10.1`, `10.2` in all images, `latest` is associated with `10.2`.


### `modellingmind/nvidia-cuda-cudnn-opengl` 
[DockerHUB link](https://hub.docker.com/repository/docker/modellingmind/cuda-cudnn-opengl)


### `modellingmind/user-layer`
[DockerHUB link](https://hub.docker.com/repository/docker/modellingmind/cuda-cudnn-opengl-userlayer)


### `modellingmind/steam-games`
[DockerHUB link](https://hub.docker.com/repository/docker/modellingmind/cuda-steam-gaming)


### `modellingmind/gpu-dev-pycharm`
[DockerHUB link](https://hub.docker.com/repository/docker/modellingmind/gpu-dev-pycharm)

Start interactive session:
```bash
docker-compose -f gpu-dev-pycharm/docker-compose.yml run dev
```

Start ssh service (background):
```bash
docker-compose -f gpu-dev-pycharm/docker-compose.yml up -d ssh
```

Kill ssh service:
```bash
docker-compose -f gpu-dev-pycharm/docker-compose.yml down ssh
```
