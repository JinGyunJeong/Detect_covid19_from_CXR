# Detect_covid19_from_CXR

## 사용 모델 : 
- Inception_Resnet_V2 사전 훈련모델의 feature_model -- 218MB -- lfs
- initial model --> tensorflow_hub
- final_model --> keras.applications

- CXR 이미지를 분류할 분류모델 --3MB

### Covid19_prediction_with_CXR.ipynb /code review
 
- 함수 하나로 구성된 코드로 예측을 수행할 CXR 이미지의 경로,
- feature_model의 경로, 분류기 모델의 경로를 차례로 파라미터로 넣어주면
- COVID19, NORMAL, PNEUMONIA 세 가지로 분류하게 된다. 정확도는 95%임을 확인하였다.

### InceptionResnet.ipynb /code review
- feature_model에 inceptionResnet_V2의 feature_model을 다운로드 받고 변수에 저장한다.
- imageDataGenerator로 파일의 전처리를 수행한 후 하나씩 feature_model로 예측을 수행한 후
리스트로 저장한다. (train/ valid set)
- 분류기 모델에 특징을 분석한 리스트를 훈련과 검증 데이터로 입력 후 모델을 훈련시킨다. -- 정확도 약 95%
- 모델을 사용하여 예측을 진행한다. 

----------------------------------------------------------------------
### HeatMap+Prediction-inception_Resnet_V2.ipynb /code review
- feature_model과 model을 지정된 경로에서 load하여 사용한다. tensorflow_hub는 사용하지 않았다.
- feature_vector에서 판단의 근거가 된 특징부분을 heatmap으로 나타내었다. CAP(Class Activation Mapping)


## 사용데이터
initial_model<br>
- CXR이미지3클래스_각 약1000개 (covid19 , normal, pneumonia)<br>
- reference : kaggle datasets<br>
- https://www.kaggle.com/prashant268/chest-xray-covid19-pneumonia
- https://www.kaggle.com/tawsifurrahman/covid19-radiography-database.

final_model : CXR이미지 (covid19 : 1300, normal : 5000, pneumonia : 5000)
- reference : kaggle datasets
- https://www.kaggle.com/prashant268/chest-xray-covid19-pneumonia
- https://www.kaggle.com/tawsifurrahman/covid19-radiography-database.
- https://www.kaggle.com/praveengovi/coronahack-chest-xraydataset
## result
- initial model<br>
예측 정확도 : 96.55% <br>

- final_model <br>
accuracy : 99.03%, loss : 0.05<br>
- confusion matrix<br>
![screenshot_20171221-151714](https://github.com/whiteBerryJ/Detect_covid19_from_CXR/blob/master/covid_model_and_result_final/Confusion_matrix_covid_normal_pneumonia.png)
