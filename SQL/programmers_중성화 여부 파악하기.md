https://school.programmers.co.kr/learn/courses/30/lessons/59409

보호소의 동물이 중성화되었는지 아닌지 파악하려 합니다.  
중성화된 동물은 **SEX_UPON_INTAKE 컬럼에 'Neutered' 또는 'Spayed'라는 단어**가 들어있습니다.  
동물의 **아이디와 이름, 중성화 여부**를 **아이디 순**으로 조회하는 SQL문을 작성해주세요.  
이때 **중성화가 되어있다면** 'O', **아니라면** 'X'라고 표시해주세요.


```
SELECT ANIMAL_ID, NAME, 'O' AS '중성화'
FROM ANIMAL_INS
WHERE SEX_UPON_INTAKE LIKE "%Neutered%" or SEX_UPON_INTAKE LIKE "%Spayed%"
UNION
SELECT ANIMAL_ID, NAME, 'X' AS '중성화'
FROM ANIMAL_INS
WHERE SEX_UPON_INTAKE NOT LIKE "%Neutered%" AND SEX_UPON_INTAKE NOT LIKE "%Spayed%"
ORDER BY ANIMAL_ID
```

- 정규표현식 REGEXP 사용
```
SELECT
    ANIMAL_ID,
    NAME,
    IF(SEX_UPON_INTAKE REGEXP '^Neutered|^Spayed', 'O', 'X') AS '중성화'
FROM
    ANIMAL_INS;
```
