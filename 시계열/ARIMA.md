## ARIMA
- Autoregressive Integrated Moving Average
- 시계열 데이터를 분석하고 예측하기 위한 통계적 모델
- 세 가지 주요 구성 요소를 포함합니다: AR(Autoregressive), I(Integrated), MA(Moving Average)
- 각 구성 요소는 시계열 데이터의 특정 패턴을 설명하는 데 사용

---

### AR (Autoregressive)
- 자기회귀: 현재 값이 과거 값의 선형 결합으로 표현된다는 가정
- 모델 형태 : ![image](https://github.com/i2mmmmm/Study/assets/106386971/674c4395-2004-4db3-8454-d792f677bd47)
- 주요 특징: 데이터의 자기상관(자신의 과거 값과의 상관 관계)을 설명
  
**즉, 과거 값으로 현재 값을 예측**

---

### I (Integrated)
- 차분: 시계열 데이터를 안정화하기 위해 사용하는 방법, 보통 비정상적(non-stationary) 데이터의 추세를 제거하기 위해 사용
- 모델 형태: 차분을 통해 데이터를 변환한 후 ARMA 모델을 적용
  - ex) 1차 차분 : ![image](https://github.com/i2mmmmm/Study/assets/106386971/9e44fc29-1580-4ab4-900b-75a875c4a52e)
- 주요 특징: 데이터의 평균이 시간에 따라 일정하지 않을 때 이를 제거하여 시계열 데이터를 안정화
  
**즉, 차분을 통해 비정상성을 제거**

---

### MA (Moving Average)
- 이동 평균: 현재 값이 과거 오차 항의 선형 결합으로 표현된다는 가정
- 모델 형태: ![image](https://github.com/i2mmmmm/Study/assets/106386971/6780f1ab-b8cb-46d3-83d8-0dd84228fa27)
  - 여기서 𝜃𝑖 는 이동 평균 계수, 𝜖𝑡 는 백색 잡음
- 주요 특징: 시계열 데이터의 불규칙성이나 잡음을 설명
  
**즉, 과거 오차로 현재 값을 예측**

---

### ARIMA 모델의 형태
- ARIMA(p, d, q) 모델에서 𝑝,𝑑,𝑞 는 각각 AR, I, MA의 차수를 나타냄
- 𝑝 는 자기회귀 항의 수
- 𝑑 는 차분의 수
- 𝑞 는 이동 평균 항의 수
- ex) ARIMA(2, 1, 1) 모델은 2차 자기회귀, 1차 차분, 1차 이동 평균 항을 포함
