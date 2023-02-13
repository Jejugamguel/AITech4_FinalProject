![header](https://capsule-render.vercel.app/api?type=rect&color=0:DB7093,100:D3D3D3&text=도로%20유지%20보수를%20위한%20파손%20감지%20서비스&fontSize=32)
<div align="left">
	<img src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=Python&logoColor=white" />
	<img src="https://img.shields.io/badge/Pytorch-EE4C2C?style=flat&logo=Pytorch&logoColor=white" />
	<img src="https://img.shields.io/badge/OpenMMLab-181717?style=flat&logo=Github&logoColor=white" />
	<img src="https://img.shields.io/badge/FastAPI-009688?style=flat&logo=FastAPI&logoColor=white" />
	<img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=Streamlit&logoColor=white" />
	<img src="https://img.shields.io/badge/GoogleCloud-4285F4?style=flat&logo=GoogleCloud&logoColor=white" />
	<img src="https://img.shields.io/badge/Flutter-02569B?style=flat&logo=Flutter&logoColor=white" />
   
</div>
&nbsp;

# Members
- **김도윤**  : Classification Baseline 작성 및 실험, 데이터 전처리 및 Annotation 작업, Object Detection Model 실험, 서비스 배포를 위한 Backend
- **김윤호**  : Classification Baseline 작성 및 실험, 데이터 전처리 및 Annotation 작업, Object Detection Model 실험, 실시간 이미지 전송을 위한 Streamlit Frontend 모듈 구현
- **김종해**  : Frontend 및 Backend Pipeline 구현, 데이터 전처리 및 Annotation 작업, Object Detection Model 실험, GCS 기반 DB 구축, Google Bigquery를 활용한 데이터 Log 생성, Streamlit을 활용한 실시간 데이터 시각화, Flutter 기반 어플리케이션 개발
- **조재효**  : Frontend 및 Backend Pipeline 구현, 데이터 전처리 및 Annotation 작업, Object Detection Model 실험
- **허진녕**  : Classification Baseline 작성 및 실험, 데이터 전처리 및 Annotation 작업, Object Detection Model 실험 

&nbsp;

# 프로젝트 개요
> 폭설, 폭우, 도로의 노후화로 생긴 포트홀은 수많은 운전자를 위협하고 있습니다. 아스팔트 도로 위의 포트홀은 차량을 파손할 뿐만 아니라, 운전자 역시 크게 다치거나 사망하는 인명사고로 이어질 수 있습니다.
하지만 지구 둘레의 약 2.8배인 아스팔트 도로 위에서, 포트홀이 어디에 있는지 알기는 쉽지 않습니다.  
이러한 문제를 해결하고자, 인공지능을 활용하여 방대한 아스팔트 도로를 빠르게 점검하고 포트홀을 감지하는 서비스를 고안하였고, 이는 신속한 도로 유지보수를 가능하게 할 것입니다.

&nbsp;


# Repository 구조
```
├─ input
│  ├─ train
│  │  └─ 0000.png
│  ├─ test
│  │  └─ 0000.png
│  └─ annotation
│     ├─ train.json
│     └─ test.json
│
└─ final_project
   ├─ .git  
   ├─ apk
   │  ...
   │  └─ main.dart
   ├─ app
   │  ├─ routers
   │  │  └─ Det.py
   │  ├─ main.py
   │  └─ frontend.py
   ├─ classification
   ├─ mmdetection
   ├─ notebook
   ├─ script
   └─ .gitignore
```	

&nbsp;

# 프로젝트 수행 절차
<img width="600" alt="image" src="https://user-images.githubusercontent.com/93418123/218273807-b88c77e1-26a6-47e6-9a02-5db8afc68079.jpg">


&nbsp;

# Dataset
### **AIHub 개방 데이터셋**
<a href="https://aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=179" height="5" width="10" target="_blank">
<img width="500" alt="image" src="https://user-images.githubusercontent.com/69153087/217480126-21b2d495-89f7-4f23-b200-6d095150c884.png">
</a>
<a href="https://aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=178" height="5" width="10" target="_blank">
<img width="500" alt="image" src="https://user-images.githubusercontent.com/69153087/217480692-67586070-0a26-4635-bded-8d63e566367b.png">
</a>

&nbsp;

# Image Classification 실험 결과
|모델|Best Accuracy|모델|Best Accuracy|
|------|---|------|---|
|EfficientNet_b1|90.25|MobileNet_large|87.05|
|EfficientNet_b2|91.35|ResNet50|87.98|
|MobileNet_small|73.94|ResNeSt|90.02|

- __최종 모델 : EfficientNet_b2__

&nbsp;

# Annotation Tool
- Object Detection을 수행하기 위한 Annotation 작업 진행
   - 데이터 검수 결과, 불규칙적인 Annotation임을 확인
   - 자체 Annotation rules를 수립하여 작업 진행
   - 저작도구 : Computer Vision Annotation Tool (CVAT)

<a href="https://www.cvat.ai/" height="5" width="10" target="_blank">
<img width="150" alt="image" src="https://user-images.githubusercontent.com/69153087/217476587-2eccb51c-c5c3-436a-bd8a-7f217fdcc14b.png">
</a><br>
<img width="600" alt="image" src="https://user-images.githubusercontent.com/69153087/217484193-ae6fac26-2419-4a4e-b219-714184e32f43.png">

&nbsp;

# Object Detection 실험 결과
|1 stage 모델|Best mAP50|2 stage 모델|Best mAP50|
|------|---|------|---|
|YOLOF|0.3250|Cascade_rcnn_r101|0.4590|
|YOLOX|0.4610|Cascade_ConvNeXt|0.4800|
|YOLOV7|0.5293|Cascade_SwinL|0.5860|

- __최종 모델 : Cascade_Swin_Large__

&nbsp;

# Service Architecture
<img width="600" alt="image" src="https://user-images.githubusercontent.com/69153087/217483664-6cfcf439-6406-4fb9-9687-5a4a1c1203e1.png">

1. 데이터 수집
   - 차량 영상기록장치가 주기적으로 아스팔트 도로를 촬영
   - 이미지와 그 때의 위치정보를 Backend 서버로 전송
2. 모델개발 및 Backend 서버구축
   - Object Detection 모델을 활용하여, 전송받은 이미지 속 포트홀을 탐지
   - 포트홀이 존재할 경우 메타데이터를 생성
3. 데이터저장 및 로그관리
   - 이미지 고유아이디, 시간, 이미지 속 포트홀 위치, 이미지 촬영 시 위도와 경도를 포함하는 메타데이터 생성
   - 메타데이터는 Bigquery에 로그로서 기록되고, 이미지와 함께 Google Cloud Storage에 저장
4. 데이터관리
   - DB에 저장된 데이터를 지도 상에서 한 눈에 확인 가능
   - 유지보수 Manager는 '보수완료' 버튼을 통해 지도 상에서 데이터 삭제 가능

&nbsp;

# 시연영상
![시연영상](https://user-images.githubusercontent.com/69153087/217509028-50d45690-90d9-427e-b4f6-a6afcaafa3d5.gif)
![20230208151451_f4dd945c (1)](https://user-images.githubusercontent.com/69153087/217509929-ded87c38-e688-465a-a944-2ee6b9cf3227.jpg)