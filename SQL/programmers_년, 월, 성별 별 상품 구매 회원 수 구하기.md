https://school.programmers.co.kr/learn/courses/30/lessons/131532



USER_INFO 테이블과 ONLINE_SALE 테이블에서 년, 월, 성별 별로  
상품을 구매한 회원수를 집계하는 SQL문을 작성해주세요.  
결과는 년, 월, 성별을 기준으로 오름차순 정렬해주세요.  
이때, 성별 정보가 없는 경우 결과에서 제외해주세요.


```
SELECT YEAR(SALES_DATE) AS YEAR,
        MONTH(SALES_DATE) AS MONTH,
        GENDER,
        COUNT(DISTINCT U.USER_ID) AS USERS
FROM USER_INFO U RIGHT JOIN ONLINE_SALE O
ON U.USER_ID = O.USER_ID
GROUP BY YEAR(SALES_DATE), MONTH(SALES_DATE), GENDER
HAVING GENDER IS NOT NULL
ORDER BY YEAR, MONTH, GENDER 
```
