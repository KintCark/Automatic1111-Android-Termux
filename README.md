it works on current Ubuntu setup python 3.10 is back


Install stable-diffusion-webui on Termux (Android) + PRoot
This will guide you on installing AUTOMATIC1111/stable-diffusion-webui on Termux (Android) + native Make sure that you have a high-end phone to actually make this usable. On my phone with 8GB RAM, launch the webui alone take at least ~ 2 GB RAM, thus making it impossible to load any model and process further.


pkg update && pkg upgrade -y && pkg pkg install git cmake python wget && pkg install libwebp && pkg install nodejs && npm install -g npm@12.0.1 -g pnpm



1. Prerequisites
First you have to install Termux and install PRoot. Then install and login to Ubuntu in PRoot

2. Installing AUTOMATIC1111/stable-diffusion-webui

Run below commands sequentially as root user in Ubuntu

Clone the repository

git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui 



Change the current directory

cd stable-diffusion-webui 


'Fix' the issue with Python running in PRoot

export ANDROID_DATA=anything 

Install required Python packages

pkg install ninja

pip install -r requirements.txt 

Install xformers. This package is not required, but is recommended to be installed

pip install xformers 

Launch the webui. It will take some time to complete first-time installation then everything should be fine

cd stable-diffusion-webui && python launch.py --skip-torch-cuda-test --precision full --enable-insecure-extension-access --use-cpu all --opt-sdp-attention --opt-split-attention --upcast-sampling --autolaunch --theme=dark --no-half --no-gradio-queue --disable-model-loading-ram-optimization



Navigate to the webui in your browser
http://127.0.0.1:7860 

To start after rebooting termux after first installation 

cd ubuntu-in-termux && ./startubuntu.sh

THEN PASTE BOTTOM COMMAND 
cd ubuntu-in-termux && ./startubuntu.sh
cd stable-diffusion-webui && python launch.py --skip-torch-cuda-test --use-cpu all --opt-split-attention --opt-sub-quad-attention --medvram --always-batch-cond-uncond














