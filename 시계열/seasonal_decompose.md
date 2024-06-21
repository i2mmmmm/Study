## seasonal_decompose 함수

시계열 분석에서 매우 유용한 도구로, 시계열 데이터를 구성 요소로 분해하여 더 자세히 분석할 수 있게 도와주는 함수  
이를 통해 데이터 패턴 이해, 예측 모델을 개선

`import statsmodels.api as sm`

시계열 데이터 분해 예시  
`ds = sm.tsa.seasonal_decompose(df['column_name'], model='additive', period=2)`  
시각화  
`fig = ds.plot()`  
`plt.show()`  

---
### 사용하는 경우

- **시계열 데이터의 패턴 분석**: 시계열 데이터를 계절성(Seasonality), 추세(Trend), 잔차(Residuals)로 분해하여 데이터의 구조를 이해해야 할 때
- **예측 모델 개선**: 데이터를 구성 요소로 분해하여 각각의 구성 요소를 개별적으로 분석하고 예측 모델을 개선할 때
- **이상 탐지**: 잔차(Residuals)를 분석하여 이상치나 변칙적인 패턴을 탐지해야 할 때

---

### 주요 개념

- **추세(Trend)**: 데이터의 장기적인 경향
- **계절성(Seasonality)**: 데이터의 주기적인 변동
- **잔차(Residuals)**: 추세와 계절성을 제거한 후 남은 데이터로, 불규칙적인 변동

---

### 파라미터
- **model**: 'additive' 또는 'multiplicative' 모델 중 선택
  - **'additive'** 구성 요소가 더해지는 형태를 가정
  - **'multiplicative'** 모델은 구성 요소가 곱해지는 형태를 가정
- **period**: 계절 주기 설정
  - 데이터의 주기를 나타내는 값으로, 데이터를 분석하여 적절한 값을 설정해야 함
