## Environment

### Docker
#### Use

```bash
my_docker_name=itaowei/ccrep:23_02_22
local_path=$HOME
docker pull $my_docker_name
docker run --runtime=nvidia -u taow -it --ipc=host --net=host -v $local_path:/home/taow $my_docker_name
```

If you do not config your git profile, please run:

```bash
eval `ssh-agent -s`
ssh-add ~/.ssh/id_ed25519_ccrep
```

#### Build
```bash
docker_image_base=pytorch/pytorch:1.8.0-cuda11.1-cudnn8-devel
docker pull $docker_image_base
docker run -t -i $docker_image_base /bin/bash
```

```bash
# Common operations
apt-get update
apt-get install sudo -y
apt-get install vim -y
python -m pip install --upgrade pip

# update Python version to what we what
python -V # Python 3.8.8

### pip install ...
### if Tencent Server:  -i https://mirrors.cloud.tencent.com/pypi/simple
### if Uni. Server: -i 
pip install allennlp==2.8.0
pip install allennlp-models==2.8.0 -i https://mirrors.cloud.tencent.com/pypi/simple
pip install numpy==1.22.3 nltk==3.5 transformers==4.12.5 scipy==1.8.0 tokenizers==0.10.3 checklist==0.0.11 pyarrow==7.0.0 spacy==3.1.5 unidiff==0.7.3 sumeval==0.2.2 -i https://mirrors.cloud.tencent.com/pypi/simple
pip install jsonnet==0.18.0

# jupyter
pip install jupyter
pip install notebook
pip install wandb
pip install jupyter_contrib_nbextensions -i https://mirrors.cloud.tencent.com/pypi/simple
jupyter contrib nbextension install --user

### add environment variable
export PYTHONIOENCODING=utf-8 >> /root/.bashrc

# ### update torch
# pip install torch==1.13 # -i https://mirrors.cloud.tencent.com/pypi/simple
# # Successfully installed nvidia-cublas-cu11-11.10.3.66 nvidia-cuda-nvrtc-cu11-11.7.99 nvidia-cuda-runtime-cu11-11.7.99 nvidia-cudnn-cu11-8.5.0.96 torch-1.13.0

### users
useradd -d /home/taow -m --uid 1803 taow
vim /etc/sudoers # taow    ALL=(ALL:ALL) ALL

sudo apt install unzip
sudo apt install git

exit
```

```bash
container_id=6b569bc22b84
my_docker_name=itaowei/ccrep:23_02_22
docker commit -m "install git" $container_id $my_docker_name
docker login -u itaowei -p jwLiXeE28Rung8g
docker push $my_docker_name
```

## Run

### Preprocessing

```bash
# download from https://drive.google.com/file/d/1s4k2KT3p7XrnxbDXvTvzhQexxLCk4dQd/view?usp=share_link to CCRep/
unzip CCRep-data.zip
```