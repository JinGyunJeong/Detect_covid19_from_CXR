# Detect_covid19_from_CXR

### 사용 모델 : 
- Inception_Resnet_V2 사전 훈련모델의 feature_model --208MB url로 가져오기
- CXR 이미지를 분류할 분류모델 --3MB -- 파일 첨부

### Covid19_prediction_with_CXR.ipynb 코드 설명
- 함수 하나로 구성된 코드로 예측을 수행할 CXR 이미지의 경로,
feature_model의 경로, 분류기 모델의 경로를 차례로 파라미터로 넣어주면
COVID19, NORMAL, PNEUMONIA 세 가지로 분류하게 된다. 정확도는 95%임을 확인하였다.

### InceptionResnet.ipynb 코드설명
- feature_model에 inceptionResnet_V2의 feature_model을 다운로드 받고 변수에 저장한다.
- imageDataGenerator로 파일의 전처리를 수행한 후 하나씩 feature_model로 예측을 수행한 후
리스트로 저장한다. (train/ valid set)
- 분류기 모델에 특징을 분석한 리스트를 훈련과 검증 데이터로 입력 후 모델을 훈련시킨다. -- 정확도 약 95%
- 모델을 사용하여 예측을 진행한다. 

### 사용데이터
- CXR이미지3클래스_각 약1000개 (covid19 , normal, peumonia)
- 출처 : kaggle datasets
- https://www.kaggle.com/prashant268/chest-xray-covid19-pneumonia? --> covid19 사진만 test/train 에서 모두 가져옴
- https://www.kaggle.com/tawsifurrahman/covid19-radiography-database --> 모든 images를 다 사용하였다.

## result
예측 정확도 : 96.55% <br>
![screenshot_20171221-151714](https://github.com/whiteBerryJ/Detect_covid19_from_CXR/blob/master/best_accuracy.PNG)
