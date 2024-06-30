# Project-YOLOv10 (Helmet Safety Detection)
## 1. Use Google Colab as environment to install, execute code and Enable GPU for Google Colab
## 2. Download dataset 
``` bash
!gdown '1twdtZEfcw4ghSZIiPDypJurZnNXzMO7R'
```
## 3. Unzip the dataset into the datasets folder
``` bash
!gdown '1twdtZEfcw4ghSZIiPDypJurZnNXzMO7R'
!mkdir safety_helmet_dataset
!unzip -q '/content/Safety_Helmet_Dataset.zip' -d '/content/safety_helmet_dataset'
```
## 4. Install and import necessary libraries
``` bash
!git clone https://github.com/THU-MIG/yolov10.git
%cd yolov10
!pip install -q -r requirements.txt
!pip install -e .
```
## 5. Initialize YOLOv10 model
``` bash
!wget https://github.com/THU-MIG/yolov10/releases/download/v1.1/yolov10n.pt
```
initialize model from downloaded weights
``` bash
from ultralytics import YOLOv10
MODEL_PATH = 'yolov10n.pt'
model = YOLOv10(MODEL_PATH)
```
## 6. Model training
``` bash
YAML_PATH = '/content/safety_helmet_dataset/data.yaml'
EPOCHS = 50
IMG_SIZE = 256
BATCH_SIZE = 16
model.train(data = YAML_PATH , epochs = EPOCHS , batch = BATCH_SIZE , imgsz = IMG_SIZE )
```
## 7. Model Evaluation
```bash
TRAINED_MODEL_PATH = 'runs/detect/train/weights/best.pt'
model = YOLOv10 (TRAINED_MODEL_PATH)

model.val( data = YAML_PATH , imgsz = IMG_SIZE, split ='test')
```