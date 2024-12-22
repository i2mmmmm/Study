https://school.programmers.co.kr/learn/courses/30/lessons/59411

입양을 간 동물 중, 보호 기간이 **가장 길었던 동물 두 마리의 아이디와 이름**을 조회하는 SQL문을 작성해주세요.  
이때 결과는 **보호 기간이 긴 순**으로 조회해야 합니다.


```
SELECT I.ANIMAL_ID, I.NAME
FROM ANIMAL_INS I JOIN ANIMAL_OUTS O
ON I.ANIMAL_ID = O.ANIMAL_ID
ORDER BY (O.DATETIME - I.DATETIME) DESC
LIMIT 2;
```
