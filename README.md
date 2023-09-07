# Web application count people
### to create env and use this code You need to create 3 envs with anaconda. 
1. env for run web app use flask and dash.
2. env for backend code count people.
3. env for call effnet api.

### env for web app
```
screen -S runweb
conda create -n runweb python=3.9.7
conda activate runweb
conda install -c anaconda flask
conda install -c conda-forge opencv
conda install -c anaconda pandas
conda install -c anaconda csvkit
conda install -c anaconda dash
conda install -c conda-forge opencv
conda install -c conda-forge moviepy
```
### env for backend code count people
(if you in env runweb you must be deactivate env back to base for create new env.)
```
conda create -n openmmpose python=3.8 -y
conda activate openmmpose
"If you need to use jupyter notebook"
pip install --user ipykernel
python -m ipykernel install --user --name=openmmpose

conda install cython
conda install -c pytorch pytorch=1.7.0 torchvision cudatoolkit=10.2
python -c '
import torch
print(torch.__version__)
print(torch.cuda.is_available()) #Output have to be "True"
print(torch.empty((1, 2), device=torch.device("cuda")))'
python -c 'import torchvision;print(torchvision.__version__)'

pip install mmcv-full -f https://download.openmmlab.com/mmcv/dist/cu102/torch1.7/index.html

mkdir pose
cd pose
git clone https://github.com/open-mmlab/mmpose.git
mv mmpose mmpose-project 
cd mmpose-project
pip install -r requirements.txt
pip install -v -e .
"for coppy file to use in your location"
# scp -r ./mmpose  ../
cd ..

pip install mmdet==2.28.2

conda install natsort
```
### env for call effnet api
```
screen -S effnet
conda create --name usai python=3.6.9
conda activate usai
pip install -U --pre efficientnet
pip install tensorflow-gpu==2.2.0
pip install keras==2.4.3
pip install pandas
pip install Pillow
pip install scikit-image
conda install cudatoolkit=10.1.243
```
