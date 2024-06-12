## 1. 배깅 (Bagging)
Bootstrap Aggregating의 줄임말로, 데이터의 부트스트랩 샘플링을 통해 여러 모델을 학습시키고 그 예측을 평균내거나 투표를 통해 최종 결정을 내리는 방법  
예시: 랜덤 포레스트 (Random Forest)

## 2. 부스팅 (Boosting)
이전 모델이 만든 오류를 수정해 나가는 방식으로, 일련의 모델들을 순차적으로 학습  
각 모델은 이전 모델의 오류를 줄이는 방향으로 가중치를 조정해 학습  
예시: AdaBoost, Gradient Boosting Machines (GBM), XGBoost, LightGBM, CatBoost

## 3. 스태킹 (Stacking)
서로 다른 유형의 모델들을 결합하여 예측  
각 모델의 예측 결과를 메타 모델에 입력으로 사용하여 최종 예측  
- 구조:
1차 모델 (Base Learners): 서로 다른 알고리즘을 사용하는 여러 모델
메타 모델 (Meta Learner): 1차 모델의 예측 결과를 바탕으로 최종 예측을 수행하는 모델

## 4. 보팅 (Voting)
여러 모델의 예측 결과를 취합하여 최종 예측  
분류 문제에서 자주 사용되며, 모델의 예측 결과를 다수결(하드 보팅)이나 평균(소프트 보팅) 방식으로 결합  
예시: 다수결 보팅 (Hard Voting), 확률 기반 보팅 (Soft Voting)

## 5. 랜덤 서브스페이스 (Random Subspace)
각 모델이 원래 특징 공간의 무작위 하위 집합에 대해 학습하는 방식  
랜덤 포레스트의 변형

## 6. 랜덤 패치 (Random Patches)
데이터의 샘플과 특징 모두 무작위로 선택하여 여러 모델을 학습시키는 방법  
이 방법은 데이터와 특징의 무작위성을 모두 활용

## 7. 배게이팅 (Bayesian Model Averaging)
여러 모델의 예측을 조합할 때 베이지안 확률론을 사용하여 각 모델의 가중치를 설정

## 8. 블렌딩 (Blending)
스태킹과 유사하지만, 보통 훈련 데이터를 두 개의 서브셋으로 나눠서 한 서브셋에서 1차 모델을 학습시키고 다른 서브셋에서 메타 모델을 학습시키는 방법