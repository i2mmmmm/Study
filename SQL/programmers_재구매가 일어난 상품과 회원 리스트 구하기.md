https://school.programmers.co.kr/learn/courses/30/lessons/131536


ONLINE_SALE 테이블에서 **동일한 회원이 동일한 상품을 재구매**한 데이터를 구하여,  
재구매한 회원 ID와 재구매한 상품 ID를 출력하는 SQL문을 작성해주세요.  
결과는 **회원 ID**를 기준으로 **오름차순** 정렬해주시고  
회원 ID가 같다면 **상품 ID**를 기준으로 **내림차순** 정렬해주세요.


```
SELECT USER_ID, PRODUCT_ID
FROM ONLINE_SALE
GROUP BY USER_ID, PRODUCT_ID
HAVING COUNT(SALES_DATE) >=2
ORDER BY 1, 2 DESC
```
