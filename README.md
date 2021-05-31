# ingredients-classification


# Yolov5를 이용한 식재료 객체탐지 모델
상명대학교 SW-PBL 프로젝트 <br />
- email address : opea5954@gmail.com <br />
- Demo Video : https://youtu.be/o9u2amtgCto <br />

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

## Usage
yolov5 설치
```bash
!git clone https://github.com/zldrobit/yolov5.git
```

requirements.txt 설치
```bash
%cd /content/yolov5/
pip install -r requirements.txt
```


