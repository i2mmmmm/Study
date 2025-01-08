https://school.programmers.co.kr/learn/courses/30/lessons/62284

데이터 분석 팀에서는 **우유(Milk)와 요거트(Yogurt)를 동시에 구입한 장바구니**가 있는지 알아보려 합니다.  
우유와 요거트를 동시에 구입한 장바구니의 **아이디를 조회**하는 SQL 문을 작성해주세요.  
이때 결과는 장바구니의 **아이디 순**으로 나와야 합니다.

```
SELECT CART_ID
FROM (SELECT CART_ID, NAME
    FROM CART_PRODUCTS
    WHERE NAME = 'Milk'
    UNION
    SELECT CART_ID, NAME
    FROM CART_PRODUCTS
    WHERE NAME = 'Yogurt') AS TEMP
GROUP BY CART_ID
HAVING COUNT(*) = 2
ORDER BY CART_ID ASC
```
```
SELECT CART_ID
FROM CART_PRODUCTS
WHERE NAME IN ('Yogurt', 'Milk')
GROUP BY CART_ID
HAVING COUNT(DISTINCT NAME) >= 2
ORDER BY CART_ID ASC
```
