# Yolov5를 이용한 식재료 객체탐지 모델
상명대학교 SW-PBL 프로젝트 <br />
- email address : opea5954@gmail.com <br />
- Demo Video : https://youtu.be/o9u2amtgCto <br />
![image](https://user-images.githubusercontent.com/68915940/120200196-06ff2c00-c25f-11eb-87b8-62c5639d7649.png)
![image](https://user-images.githubusercontent.com/68915940/120200207-09618600-c25f-11eb-903f-284e85cecf99.png)
![image](https://user-images.githubusercontent.com/68915940/120200219-0b2b4980-c25f-11eb-8dc0-6fb6f2c3a34e.png)

## Introduction
Yolov5와 Tensorflow Lite를 기반으로한 레시피 추천 어플리케이션
1. Yolov5로 학습한 식재료 탐지 모델을 이용하여 실시간으로 식재료 탐지
2. 현재까지 인식한 식재료 중 가장 연관성 높은 요리를 실시간으로 제공
3. 연관성 높은 요리의 레시피를 볼 수 있는 사이트 링크 제공

## Development Environment
- Google colaboratory
- Yolov5
- Tensorflow 1.15.2v
- Android Studio @3.5.3

## Food ingredients dataset
1. Class : 11
    - 마늘, 감자, 달걀, 양파, 닭고기, 돼지고기, 대파, 소고기, 김치, 햄, 콩나물
    
![image](https://user-images.githubusercontent.com/68915940/120200231-0e263a00-c25f-11eb-8b11-cf887a5f492e.png)


2. Images : 905
3. TRAIN/TEST SPLIT(100%) 
    - Train : 631(70%)
    - Valid : 179(20%)
    - Test : 95(10%)
    
![image](https://user-images.githubusercontent.com/68915940/120195304-93a6eb80-c259-11eb-8743-99db1c743449.png)
    
Dataset download : https://drive.google.com/file/d/1TMjSp__xeLrYLKl-XmWTIy10e4tXcjHB/view?usp=sharing

## Model Training
1. yolov5 설치
```bash
!git clone https://github.com/zldrobit/yolov5.git
```

2. requirements.txt 설치
```bash
%cd /content/yolov5/
pip install -r requirements.txt
```

3. Model 학습
```bash
!python train.py --img 416 --batch 16 --epochs 300 --data /content/data.yaml --cfg ./models/yolov5s.yaml --weights yolov5s.pt --name food_ingredients_model
```

(요기부턴 안드로이드 연동)
4. https://github.com/zldrobit/yolov5 이동
 models/tf.py 파일을 colab의 /content/models/ 디렉터리에 저장
 
5. 학습된 가중치 파일(.pt)를 .tflite로 변환
```bash
!PYTHONPATH=. python models/tf.py --weights runs/train/food_ingredients_model/weights/best.pt --cfg models/yolov5s.yaml --img 320
```

## Android 연동
1. yolov5 app 변경
yolov5의 app의 내용을 
https://github.com/Q-100/ingredients-classification.git 로 변경

2. assets에 Model Training에서 학습한 best-fp16.tflite 파일 저장
또는 
weight(.tflite) 
https://drive.google.com/file/d/1lvwR8SvFC8moYsfMrxvUV1SeIQBPFx1L/view?usp=sharing 저장

3. 실행 ^^

## 코드설명
DetectorActivity.java




