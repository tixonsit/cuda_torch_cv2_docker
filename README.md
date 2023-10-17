# Stable Docker image for CV

Stable Dockerfile with:
* ubuntu 22.04
* Cuda 12.1
* Cudnn 8.9.0.131
* OpenCV 4.8.1 with Cuda support + DNN + contrib
* Pytorch 2.1 cuda, torchvision 0.16.0, torchaudio 2.1.0

## Prebuild

`docker pull tixons/opencv-cuda`

## Build from scratch

On Ubuntu you need to install [Cuda](https://developer.nvidia.com/cuda-downloads), [Docker](https://docs.docker.com/engine/install/ubuntu/), [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)
If on Windows use WSL2 and follow [this](https://ubuntu.com/tutorials/enabling-gpu-acceleration-on-ubuntu-on-wsl2-with-the-nvidia-cuda-platform#1-overview) and [this](https://docs.nvidia.com/cuda/wsl-user-guide/index.html) pages.

Build:
`docker build -t opencv-cuda:4.8.1 .`

Launch in bash:
`docker run --gpus all -it opencv-cuda:4.8.1 bash`

Test:
`python3 -c "import cv2; print(cv2.__version__); print(cv2.cuda.getCudaEnabledDeviceCount()); import torch; print(torch.__version__); print(torch.cuda.is_available())"`
`>>> 
4.8.1
1
2.1.0+cu121
True
`
