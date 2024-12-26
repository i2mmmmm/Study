https://school.programmers.co.kr/learn/courses/30/lessons/293257

FISH_NAME_INFO에서 물고기의 종류 별 **물고기의 이름과 잡은 수**를 출력하는 SQL문을 작성해주세요.

물고기의 이름 컬럼명은 FISH_NAME, 잡은 수 컬럼명은 FISH_COUNT로 해주세요.
결과는 **잡은 수 기준으로 내림차순** 정렬해주세요.

```
SELECT I.FISH_COUNT, N.FISH_NAME
FROM FISH_NAME_INFO N RIGHT JOIN(
SELECT FISH_TYPE, COUNT(ID) AS FISH_COUNT
FROM FISH_INFO
GROUP BY FISH_TYPE) I
ON N.FISH_TYPE = I.FISH_TYPE
ORDER BY FISH_COUNT DESC
```
