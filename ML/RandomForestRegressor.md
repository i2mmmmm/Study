## RandomForestRegressor

- 앙상블 학습 방법 중 하나로, 여러 개의 결정 트리를 결합하여 회귀 문제를 해결하는 모델
- 랜덤 포레스트(Random Forest)의 회귀 버전
  - 랜덤 포레스트는 여러 결정 트리(decision tree)로 구성, 데이터를 분할하여 예측을 수행하는 비선형 모델
- 배깅(bagging)이라는 앙상블 방법을 사용
  - 부트스트랩 방법을 사용하여 여러 데이터 샘플을 생성, 각 샘플에 대해 모델을 학습, 예측 결과를 평균 또는 다수결 투표로 결합하는 방식
- 랜덤성
  - 데이터 샘플링: 각 트리를 학습시킬 때, 전체 데이터셋에서 부트스트랩 샘플링(복원 추출)으로 새로운 학습 데이터를 생성
  - 특성 선택: 각 노드를 분할할 때, 전체 특성 중 무작위로 선택된 일부 특성만을 사용하여 최적의 분할을 찾음
  - 랜덤성으로 인해 결과가 계속 다르게 나오기 때문에 파라미터로 **random_state** 를 고정시키면 같은 결과를 낼 수 있다
    
---

### 장점
- 과적합 방지: 여러 트리의 예측을 결합함으로써 모델의 분산을 줄이고 과적합을 방지
- 특성 중요도: 모델은 각 특성의 중요도를 계산할 수 있다. 이는 해석 가능성과 feature selection에 유용함
- 강력한 성능: 다양한 데이터셋에서 좋은 예측 성능을 보임
### 단점
- 복잡성: 많은 트리를 생성하므로, 학습과 예측이 느릴 수 있다.
- 해석 어려움: 개별 트리와 달리, 랜덤 포레스트는 복잡하여 해석이 어렵다.

---

### 주요 하이퍼파라미터
- n_estimators: 생성할 트리의 개수. 일반적으로 많을수록 성능이 좋지만, 학습 시간과 메모리 사용량이 증가
- max_depth: 각 트리의 최대 깊이. 깊이가 깊을수록 모델이 복잡해지지만, 과적합 위험도 증가
- min_samples_split: 노드를 분할하기 위한 최소 샘플 수. 값이 클수록 트리가 덜 복잡
- min_samples_leaf: 리프 노드가 되기 위한 최소 샘플 수. 값이 클수록 모델의 복잡도가 낮아짐
- max_features: 각 분할에서 고려할 최대 특성 수. "auto", "sqrt", "log2" 등의 값을 가질 수 있다
- bootstrap: 부트스트랩 샘플링을 사용할지 여부 결정

---

### 예제 코드

```
from sklearn.ensemble import RandomForestRegressor
from sklearn.datasets import make_regression
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error

# 데이터 생성
X, y = make_regression(n_samples=1000, n_features=20, noise=0.1)

# 학습/테스트 데이터 분할
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 모델 초기화
rf = RandomForestRegressor(n_estimators=100, max_depth=None, min_samples_split=2, min_samples_leaf=1, max_features='auto', bootstrap=True, random_state=42)

# 모델 학습
rf.fit(X_train, y_train)

# 예측
y_pred = rf.predict(X_test)

# 성능 평가
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse}")

```

RandomForestRegressor는 강력하고 유연한 회귀 모델로, 다양한 데이터셋에서 높은 성능을 보인다.  
과적합 방지, 특성 중요도 계산 등의 장점을 가지지만, 복잡성으로 인해 해석이 어렵고 학습 시간이 오래 걸릴 수 있다.  
하지만 적절한 하이퍼파라미터 튜닝을 통해 최적의 성능을 얻을 수 있다.

**이번 예측 분석에서 사용한 예시**
```
# 모델 학습
model = RandomForestRegressor()
param_grid = {
    'max_features' : ['auto', 'sqrt', 'log2'],
    'max_depth': [8, 10, 12],
    'n_estimators': [100, 200, 300],
    'bootstrap': [True, False]
}
grid_search = GridSearchCV(model, param_grid, cv=5, scoring='r2')
grid_search.fit(X_train, y_train)

# 최적 모델로 예측
best_model = grid_search.best_estimator_
y_pred = best_model.predict(X_test)

# 성능 평가
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f'MSE: {mse}')
print(f'R2: {r2}')
```
