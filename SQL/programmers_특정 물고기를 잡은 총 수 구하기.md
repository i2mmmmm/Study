
https://school.programmers.co.kr/learn/courses/30/lessons/298518


FISH_INFO 테이블에서 잡은 BASS와 SNAPPER의 수를 출력하는 SQL 문을 작성해주세요.  
컬럼명은 'FISH_COUNT`로 해주세요.


```
SELECT COUNT(ID) AS FISH_COUNT
FROM FISH_INFO I LEFT JOIN FISH_NAME_INFO N
ON I.FISH_TYPE = N.FISH_TYPE
WHERE FISH_NAME = 'BASS' OR FISH_NAME = 'SNAPPER'
```
