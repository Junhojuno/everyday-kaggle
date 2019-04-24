# House Price Prediction

### Competition Description
> - 본 대회는 구글 코리아가 후원하고, 캐글 코리아가 진행하는 데이터 사이언스 대회입니다. 
> - Academic 목적이며, 대한민국 누구나 참여하실 수 있습니다.
> - 데이터는 미국 Kings County의 집값 데이터 입니다.

### Feature Visualization
![Competition Image](https://github.com/Junhojuno/everyday-kaggle/blob/master/houseprice_prediction/House_Price_Features.png?raw=true)

### Evaluation
- Root Mean Squared Error
![RMSE](https://github.com/Junhojuno/everyday-kaggle/blob/master/houseprice_prediction/rmse.PNG?raw=true)

### 사용한 모델
- LigthGBM

### Score
- Baseline model을 기준으로 feature importance를 뽑았을 때

| Feature Engineering | PB | LB | PB Rank | LB Rank |
| ------------- |:-------------:| -----:| ---- | ---- |
| Base Features | 109341.60599 | 110964.02797 | 194/415(45%) | 115/415(27%) |
| + Distance | 107763.85539 | 111758.13889 | 142/415(34%) | 131/415(31%) |
| + PCA + K-means | 109459.65838 | 108986.88078 | 195/415(46%) | 62/415(15%) |
| + zipcode grouping | 102080.97481 | 110991.78514 | 32/415(7%) | 118/415(28%) |
  * Distance : 가장 비싼 집에서 각 데이터까지의 거리, lat/long을 좌표로 하여 Norm을 계산
  * PCA : correlation이 높았던 변수 sqft_living, sqft_above, sqft_basement를 2차원으로 축소하였다.
  * K-means : lat/long을 기준으로 32개 지점으로 데이터를 그룹화하였다.
  * zipcode grouping : 5자리로 구성된 zipcode를 분해하여 3번째자리, 4번째자리...등으로 그룹화하였다. 

### 대회를 통해 얻는 것 / 아쉬운점
- Public Score에 맞춰 Feature Engineering을 하게 되면 Public 20%에 overfitting되어 Private에서 미끄러진다.
- EDA를 진행하기전 전체적인 Flow를 미리 한번 그려보고 진행하는 것이 생각을 정리하고 방향잡는데 도움이 된다.
- 다른 사람들의 Kernel을 참고하는 것이 중요하다. 어떤 Feature를 살펴보았는지, 어떠한 이유로 feature로 채택했는지 등등
- 대부분의 Kernel에서 Model 여러개를 적절히 섞는 Model Ensemble을 많이 사용하였다. 
- Motivation을 통해 가설을 세우고 성능을 통해 검증하는 과정이 조금 부족했던 것 같다.
