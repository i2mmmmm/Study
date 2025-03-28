### 1. GROUP BY 그룹으로 묶기

ex)
```
SELECT COUNTRY FROM CUSTOMERS
GROUP BY COUNTRY;
```
```
SELECT COUNTRY, CITY, CONCAT_WS('_', CITY, COUNTRY)
FROM CUSTOMERS
GROUP BY COUNTRY, CITY;
```
```
날짜마다 ORDER 갯수 구하기
SELECT COUNT(*), ORDERDATE
FROM ORDERS
GROUP BY ORDERDATE;
```
```
SELECT 
　　CATEGORI_ID,
　　MAX(PRICE) AS MAX_PRICE,
　　MIN(PRICE) AS MIN_PRICE,
　　TRUNCATE((MAX(PRICE)+MIN(PRICE))/2, 2) AS MEDIAN_PRICE,
　　TRUNCATE(AVG(PRICE), 1) AS AVERAGE_PRICE
FROM PRODUCTS
GROUP BY CATEGORI_ID;
```

### 2. WITH ROLLUP : 각 집계함수에 총 합계 라는 한 행 추가
-> ORDER BY 와 함께는 사용할 수 없음  
ex)
```
SELECT COUNTRY, COUNT(*)
FROM SUPPLIERS
GROUP BY COUNTRY
WITH ROLLUP;
```


### 3. HAVING : 조건문
- WHERE 은 그룹하기 전의 데이터, HAVING 은 그룹 후 집계에 사용  
ex)  
```
SELECT COUNT(*) AS COUNT, ORDERDATE
FROM ORDERS
WHERE ORDERDATE > DATE('1996-12-31')
GROUP BY ORDERDATE
HAVING COUNT > 2;
```
이런 순서로 쓰임 WHERE -> GROUP -> HAVING  
WHERE 날짜 이전의 것만 GROUP 한 다음 COUNT가 2 넘는 것을 데려오겠다.  


### 4. DISTINCT : 중복된 값들 제거
- GROUP BY 와 달리 집계함수 사용되지 않음
- GROUP BY 와 달리 정렬하지 않으므로 더 빠름 (더 가벼움, 따로 ORDER BY 사용해서 정렬 가능)
- SELECT 에서 사용

ex)
```
SELECT DISTINCT CATEGORY_ID
FROM PRODUCTS;
```
ex)
```
SELECT COUNTRY, COUNT(DISTINCT CITY)
FROM CUSTOMERS
GROUP BY COUNTRY;
이렇게 쓰면 각 나라에 중복되지 않는 도시 갯수 구하기 가능
```
