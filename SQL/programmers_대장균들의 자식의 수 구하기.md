https://school.programmers.co.kr/learn/courses/30/lessons/299305

대장균 개체의 ID(ID)와 **자식의 수(CHILD_COUNT**)를 출력하는 SQL 문을 작성해주세요.  
자식이 없다면 자식의 수는 0으로 출력해주세요. 이때 결과는 개체의 **ID 에 대해 오름차순** 정렬해주세요.

```
SELECT E.ID, COUNT(E2.PARENT_ID) AS CHILD_COUNT
FROM ECOLI_DATA E LEFT JOIN ECOLI_DATA E2
ON E.ID = E2.PARENT_ID
GROUP BY E.ID
ORDER BY E.ID
```
