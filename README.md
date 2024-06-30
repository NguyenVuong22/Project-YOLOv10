# Project-YOLOv10 (pre_trained_model)
## 1. Use Google Colab as environment to install and execute code and Enable GPU for Google Colab
## 2. Download YOLOv10 source code
``` bash
!git clone https://github.com/THU-MIG/yolov10.git
```
## 3. Install  necessary libraries
```
``` bash
%cd yolov10
!pip install -q -r requirements.txt
!pip install -e .
```
## 4. Initialize YOLOv10 model
``` bash
!wget https://github.com/THU-MIG/yolov10/releases/download/v1.1/yolov10n.pt
```
initialize model from downloaded weights
``` bash
from ultralytics import YOLOv10
MODEL_PATH = 'yolov10n.pt'
model = YOLOv10(MODEL_PATH)
```
## 5. Upload the image to be predicted
``` bash
from google.colab import files
uploaded = files.upload()
```
## 6. Predict 
```bash
IMG_PATH = '/content/yolov10/HCMC_Street.jpg'
result = model(source = IMG_PATH )[0]
```
## 7. Save prediction results
```bash
result.save ('/content/yolov10/HCMC_Street_predict.png')
```