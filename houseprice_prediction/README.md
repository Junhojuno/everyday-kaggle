## House Price Prediction

### Competition Description
> - 본 대회는 구글 코리아가 후원하고, 캐글 코리아가 진행하는 데이터 사이언스 대회입니다. 
> - Academic 목적이며, 대한민국 누구나 참여하실 수 있습니다.
> - 데이터는 미국 Kings County의 집값 데이터 입니다.

### Feature Visualization
![Competition Image](https://github.com/Junhojuno/everyday-kaggle/blob/master/houseprice_prediction/House_Price_Features.png?raw=true)

### Evaluation
- Root Mean Squared Error
![RMSE]()

### 사용한 모델
- LigthGBM

### Score
- Baseline model을 기준으로 feature importance를 뽑았을 때
| Feature Engineering | PB | LB  |
| ------------- |:-------------:| -----:|
| Base Features | 109341.60599 | 110964.02797 |
| + Distance | 107763.85539 | 111758.13889 |
| + PCA + K-means | 109459.65838 | 108986.88078 |
| + zipcode grouping with dummy | 102080.97481 | 110991.78514 |

### 대회를 통해 얻는 것
