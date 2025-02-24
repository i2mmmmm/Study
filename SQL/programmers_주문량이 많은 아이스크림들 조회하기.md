https://school.programmers.co.kr/learn/courses/30/lessons/133027


**7월** 아이스크림 총 주문량과 **상반기**의 아이스크림 총 주문량을 **더한 값**이 큰 순서대로 **상위 3개의 맛**을 조회하는 SQL 문을 작성해주세요.

```
SELECT J.FLAVOR
from JULY J LEFT JOIN (SELECT FLAVOR, SUM(TOTAL_ORDER) AS TOT
                    FROM FIRST_HALF
                    GROUP BY FLAVOR) H
ON J.FLAVOR = H.FLAVOR
GROUP BY J.FLAVOR
ORDER BY SUM(J.TOTAL_ORDER) + TOT DESC
LIMIT 3;
```
