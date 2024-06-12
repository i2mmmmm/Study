## 1. 지도 학습 (Supervised Learning)
**레이블이 달린** 데이터를 사용해 모델을 학습.  
입력 데이터와 그에 대응하는 출력 데이터를 기반으로 모델이 예측.

**대표적인 알고리즘**  
선형 회귀 (Linear Regression)  
로지스틱 회귀 (Logistic Regression)  
서포트 벡터 머신 (Support Vector Machine, SVM)  
나이브 베이즈 (Naive Bayes)  
의사결정 나무 (Decision Tree)  
랜덤 포레스트 (Random Forest)  
k-최근접 이웃 (k-Nearest Neighbors, k-NN)  
신경망 (Neural Networks)  

## 2. 비지도 학습 (Unsupervised Learning)
레이블이 **없는** 데이터를 사용해 데이터 패턴 찾거나 구조를 학습.  
주로 데이터 군집화와 차원 축소에 사용.  

**대표적인 알고리즘**  
k-평균 군집화 (k-Means Clustering)  
계층적 군집화 (Hierarchical Clustering)  
DBSCAN (Density-Based Spatial Clustering of Applications with Noise)  
주성분 분석 (Principal Component Analysis, PCA)  
t-SNE (t-Distributed Stochastic Neighbor Embedding)  

## 3. 준지도 학습 (Semi-Supervised Learning)  
레이블이 달린 데이터와 레이블이 없는 데이터를 모두 사용하는 학습 방법.  
레이블이 달린 데이터가 적고 레이블링 비용이 높을 때 유용함.

## 4. 강화 학습 (Reinforcement Learning)  
에이전트가 환경과 상호 작용하면서 보상을 최대화하는 방법을 학습.  
주로 게임, 로봇 공학, 최적화 문제에 사용됨.

**대표적인 알고리즘**  
Q-러닝 (Q-Learning)  
SARSA (State-Action-Reward-State-Action)  
DDPG (Deep Deterministic Policy Gradient)  
PPO (Proximal Policy Optimization)  

## 5. 자기 지도 학습 (Self-Supervised Learning)
모델이 데이터의 일부를 예측하도록 학습하는 방법.  
보통 데이터의 구조적 특성을 이용하여 레이블을 생성함.  
특히 자연어 처리와 컴퓨터 비전에서 많이 사용.

## 6. 전이 학습 (Transfer Learning)
사전 학습된 모델을 새로운 작업에 적응시키는 방법.  
이는 사전 학습된 모델의 지식을 활용하여 새로운 문제를 해결하는 데 유용함.

## 7. 앙상블 학습 (Ensemble Learning)
여러 모델을 결합하여 더 나은 예측 성능을 얻는 방법.  

**대표적인 알고리즘**  
배깅 (Bagging)  
부스팅 (Boosting)  
AdaBoost  
Gradient Boosting  
XGBoost  
스태킹 (Stacking)  

## 8. 온라인 학습 (Online Learning)
데이터가 연속적으로 주어질 때 실시간으로 모델을 업데이트하는 방법.  
주로 스트리밍 데이터 환경에서 유용.
