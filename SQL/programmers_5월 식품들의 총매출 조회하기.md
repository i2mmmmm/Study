https://school.programmers.co.kr/learn/courses/30/lessons/131117

FOOD_PRODUCT와 FOOD_ORDER 테이블에서 **생산일자가 2022년 5월**인 식품들의   
**식품 ID, 식품 이름, 총매출**을 조회하는 SQL문을 작성해주세요.   
이때 결과는 **총매출을 기준으로 내림차순** 정렬해주시고  
총매출이 같다면 **식품 ID를 기준으로 오름차순** 정렬해주세요.

```
SELECT P.PRODUCT_ID, P.PRODUCT_NAME, (AMNT * P.PRICE) AS TOTAL_SALES
FROM FOOD_PRODUCT P
JOIN (SELECT PRODUCT_ID, SUM(AMOUNT) AS AMNT
      FROM FOOD_ORDER
      WHERE PRODUCE_DATE LIKE '2022-05%'  
      GROUP BY PRODUCT_ID
     ) O
ON P.PRODUCT_ID = O.PRODUCT_ID
ORDER BY TOTAL_SALES DESC, PRODUCT_ID ASC
```
