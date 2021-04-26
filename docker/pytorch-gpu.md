## Steps for building a pytorch-gpu docker environment in the server. 

1. Control Docker with systemd, and HTTP/HTTPS proxy (optinal)
https://docs.docker.com/config/daemon/systemd/#httphttps-proxy

2. Pull the image 
https://hub.docker.com/ 
docker pull pytorch/pytorch:1.8.0-cuda11.1-cudnn8-devel
docker pull nvcr.io/nvidia/pytorch:21.03-py3
Then you can check the image with: docker images

3. Install the nvidia gpu container for the usage of gpu
https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html

4. Configure the Docker client
https://docs.docker.com/network/proxy/

5. Create a container for pytorch-gpu
sudo docker run --gpus all -it -v /localdir/:/containerdir/ --name my_pytorch_project pytorch/pytorch:1.8.0-cuda11.1-cudnn8-devel 
--gpus '"device=0"' (all): add this if you want to use gpu 
-v /local_dir/:/container_dir/: local_dir is the directory or file from your host system (absolute path) that you want to access from inside your container. Mount your project directory here with code and data to work on it from inside the container at the /containerdir/ path. 
--name: assign a name the container for future reference.
