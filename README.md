# Automatic1111-Android-Termux
Automatic1111 on android termux!


Install stable-diffusion-webui on Termux (Android) + PRoot
This will guide you on installing AUTOMATIC1111/stable-diffusion-webui on Termux (Android) + PRoot Distro. Make sure that you have a high-end phone to actually make this usable. On my phone with 8GB RAM, launch the webui alone take at least ~ 2 GB RAM, thus making it impossible to load any model and process further.


pkg updated && pkg upgrade -y && termux-setup-storage &&
pkg install wget -y && pkg install git -y && pkg install proot -y &&
cd ~ && git clone https://github.com/MFDGaming/ubuntu-in-termux.git && cd ubuntu-in-termux && chmod +x ubuntu.sh && ./ubuntu.sh -y && ./startubuntu.sh 



1. Prerequisites
First you have to install Termux and install PRoot. Then install and login to Ubuntu in PRoot

2. Installing AUTOMATIC1111/stable-diffusion-webui

Run below commands sequentially as root user in Ubuntu

Install basic tools
apt update && apt upgrade -y && apt-get install curl git gcc make build-essential python3 python3-dev python3-distutils python3-pip python3-venv python-is-python3 -y 

Install required extensions

apt-get install libgl1 libglib2.0-0 libsm6 libxrender1 libxext6 -y

Clone the repository

git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui 



Change the current directory

cd stable-diffusion-webui 


'Fix' the issue with Python running in PRoot

export ANDROID_DATA=anything 

Install required Python packages

pip install -r requirements.txt 

Install xformers. This package is not required, but is recommended to be installed

pip install xformers 

Launch the webui. It will take some time to complete first-time installation then everything should be fine

cd stable-diffusion-webui && python launch.py --skip-torch-cuda-test --precision full --enable-insecure-extension-access --use-cpu all --opt-sdp-attention --opt-split-attention --opt-sub-quad-attention --upcast-sampling --autolaunch --theme=dark --no-half --no-gradio-queue --disable-model-loading-ram-optimization



Navigate to the webui in your browser
http://127.0.0.1:7860 

To start after rebooting termux after first installation 

cd ubuntu-in-termux && ./startubuntu.sh

THEN PASTE BOTTOM COMMAND 
cd ubuntu-in-termux && ./startubuntu.sh
cd stable-diffusion-webui && python launch.py --skip-torch-cuda-test --use-cpu all --opt-split-attention --opt-sub-quad-attention --medvram --always-batch-cond-uncond














