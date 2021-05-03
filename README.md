# Photovoltaic_Prediction
기상 데이터를 이용하여 태양광 발전량 예측
## 설명
기상 데이터를 통해 태양광 발전량을 예측하는 머신러닝 모델입니다.<br>
세 가지 모델을 사용하여 두 종류의 예측을 합니다.

### 모델 종류
* LSTM 모델
* k-NN Regression 모델
* SVM Regression(SVR) 모델

### 만약 이 지역에 발전소가 있었다면 얼마나 발전량이 나왔을지 예측하는 가상 발전소 모델
> 이 모델은 과거 발전량 데이터와 과거 날씨 데이터의 상관관계를 분석하여<br>
절댓값이 0.1 이상인 feature만 사용하여 학습합니다.<br>
해당하는 11개의 날씨 feature, 발전량과 시간 총 13개의 feature를 사용하여 학습합니다.<br>
사용한 모델은 k-NN Regression 모델, SVR 모델입니다.<br>
정확도는 R2 score로 계산했습니다.<br>
실제값과 일치하면 1, 전혀 다르면 0의 값을 보여줍니다.<br>
* 날씨 feature와 태양광 발전량의 상관관계<br>
<img src="/img/correlation.jpg" title="correlation" alt="correlation"></img>
* 가상 발전소의 발전량 예측<br>
<img src="/img/virtual_power_plant.jpg" width="80%" height="60%" title="virtual_power_plant" alt="virtual_power_plant"></img>

<br>

### 내일 날씨 예보를 통해 내일 발전량이 얼마나 나올지 예측하는 모델
> 이 모델은 위의 모델에서 사용한 데이터 중 기상청에서 공개하는 예보 데이터인<br>
온도, 풍속, 풍향, 습도 및 발전량과 시간 총 6개의 feature를 사용하여 학습합니다.<br>
사용한 모델은 k-NN Regression 모델, SVR 모델, LSTM 모델입니다.<br>
정확도는 R2 score로 계산했습니다.<br>
실제값과 일치하면 1, 전혀 다르면 0의 값을 보여줍니다.<br>
* 내일 발전량 예측<br>
<img src="/img/tomorrow_prediction.jpg" width="80%" height="60%" title="tomorrow_prediction" alt="tomorrow_prediction"></img>


### 정확도(R2 score)
>가상 발전소 예측은 SVR 모델이 96%로 가장 높은 정확도를 보였고,<br>
내일 발전량 예측은 k-NN Regression 모델이 85%로 가장 높은 정확도를 보였습니다.

<img src="/img/R2_score.jpg" title="R2_score" alt="R2_score"></img><br>


### 코드 목록
* lstm_generation_prediction.ipynb

> 데이터 전처리 및 LSTM 모델의 설계부터 학습, 검증까지 작성한 코드입니다.<br>
Keras를 사용하여 LSTM 모델을 만들었습니다.<br>
구글 Colab에서 개발였습니다.

* ml_generation_prediction.py

> 데이터 전처리 및 k-NN Regression, SVR 모델의 설계부터 학습, 검증까지 작성한 코드입니다.<br>
sklearn을 사용하여 만들었습니다.<br>
구글 Colab에서 개발였습니다.


## 작업환경
Python3, tensorflow_version 2.x, sklearn, Google Colab

## 데이터
공공데이터포털에서 영암에 있는 F1 경기장의 태양광 발전소의 과거 발전량 데이터를,<br>
기상자료개방포털에서 F1 경기장과 약 8km 떨어진 목포 기상대의 과거 날씨 데이터를 수집했습니다.

