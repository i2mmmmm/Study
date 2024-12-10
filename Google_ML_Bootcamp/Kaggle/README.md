### 프로젝트 소개 및 회고

---

중고차 가격 예측 Kaggle 프로젝트를 진행했습니다. 평소 진행하던 Kaggle 대회들의 깔끔한 데이터와는 달리 전처리가 많이 필요한 데이터였습니다.  실제 중고차 가격이 아닌 AI를 통해 만들어진 합성 데이터였기 때문에, 전처리 과정에서 이치에 맞지 않는 데이터들을 어떻게 처리해야 할지 고민이 많았습니다.

전처리
1. fuel_type 에서 null 값은 engine을 바탕으로 분류하여 채웠습니다. (engine에 근거가 없는 행은 삭제했습니다)
2. engine 정보를 3개 열로 나누고 삭제 (engine -> horsepower, displacement, cylinder_count)
3. target 값 로그 변환 (target 값이 price 가 한쪽으로 치우침)
4. clean_title null 값 'no'로 변환
5. transmission 정보 3개 열로 나누고 삭제 (transmission -> transmission_type, transmission_speed, special_feature)
6. mode_values 열 생성 (모델별 빈도수)
7. transmission_speed 정수형 변환
8. accident, displacement, cylinder_count null 값 제거 (data 갯수 : 187,716 -> 182,058)
9. special_feature null 값 0으로 대체
10. int_col, ext_col 에 대하여 다양한 색상 줄이기 (ex: Blu, BLUE, BLU ELEOS, Stormy Sea -> Blue)
11. accident, clean_title 이진 변수에 대하여 0,1 로 값 변환
12. 브랜드별 평균 가격 변수 추가

모델링
```
predictor = TabularPredictor(label=label_column, eval_metric='rmse').fit(  
    train_data=train_data.drop(columns=['log_price']),  
    presets='best_quality',  
    time_limit=3600,  
    num_bag_folds=5
)
```
---

**대회 링크 :** https://www.kaggle.com/competitions/playground-series-s4e9

**프로젝트 기간 :** 2024.09.13 - 2024.10.01

**환경 :** **Python** ver.3.10.13 / autogluon==1.1.1

**역할 :** (2인 팀) 데이터 전처리, 모델링 (feature engineering, modeling)

**깃허브 링크 :** https://github.com/i2mmmmm/Study/tree/main/Google_ML_Bootcamp/Kaggle
