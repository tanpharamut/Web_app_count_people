# Web application count people
### to create env and use this code You need to create 3 envs with anaconda. 
1. Env for run web app use flask and dash.
2. Env for backend code count people.
3. Env for call effnet api.

### Env for web app
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
# press CTRL + A + D (quit screen)
```
### Env for backend code count people
(if you in env runweb you must be deactivate env ( conda deactivate ) back to base for create new env.)
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
### Env for call effnet api
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
# press CTRL + A + D (quit screen)
```
### Usage
First step open screen effnet for run call api.
```
screen -r effnet
python effnet_test.py
# press CTRL + A + D (quit screen)
```
Second step open screen runweb for run web app.
```
screen -r runweb
python app.py
```
Copy the URL link or CTRL + click the URL link to the web app.
1. On the web page, you can click Upload to upload your video and then click DRAW.
2. After clicking DRAW, the website status will say Uploading after the video is uploaded.
3. You will be on the labels page. on the label page You will need to draw a box in the area where you want to count the number of people. and click Save.
4. After clicking save You can click Count people to count the number of run and processing...
5. And if done, you will see the dashboard.
6. The dashboard shows total numbers, number of men, number of women, number of categories (children, students, work and disabled), charts, and Google Sheets buttons.
7. Click the Google Sheets button to see the person's duration, gender, category, and photo.

