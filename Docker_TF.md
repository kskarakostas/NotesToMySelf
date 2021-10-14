# Generic info
* https://www.tensorflow.org/install/docker
* https://github.com/NVIDIA/nvidia-docker



# Docker part
### Setting up NVIDIA Container Toolkit
```bash
distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
   && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
   && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

sudo apt-get update && sudo apt-get install -y nvidia-docker2
sudo systemctl restart docker
```

### Verify your nvidia-docker installation:
```bash
docker run --gpus all --rm nvidia/cuda nvidia-smi
```


### Download latest release w/ GPU support and Jupyter
```bash
docker pull tensorflow/tensorflow:latest-gpu-jupyter
```

### Build custom Dockerfile (AIO)
```bash
FROM tensorflow/tensorflow:latest-gpu-jupyter

RUN pip3 -q install pip --upgrade
# Install all basic packages
RUN pip3 install \
    # Jupyter itself
    jupyter \
    # Numpy and Pandas are required a-priori
    numpy pandas \
    # PyTorch with CUDA 10.2 support and Torchvision
    torch torchvision \
    # Hugging Face Transformers
    transformers \
    # Var...
    barbar sklearn livelossplot keras_sequential_ascii
```

### Start docker with Jupyter access, GPU enabled & mount the host directory and change the container's working directory (via -w)
```bash
docker run -it -p 8888:8888 -v $PWD:/tf/KGL -w /mnt/projects/KGL/TweetSentimentExtraction --gpus all tensorflow/tensorflow:latest-gpu-jupyter
```

# Python Snippets

### Generic requirements
```python
!/usr/bin/python3 -m pip install --upgrade pip
!pip install -U pandas sklearn transformers nltk

import nltk
nltk.download('stopwords')
nltk.download('wordnet')
```

### Suppress TF2 warnings

```python
import logging, os

logging.disable(logging.WARNING)
os.environ["TF_CPP_MIN_LOG_LEVEL"] = "3"
```

