https://school.programmers.co.kr/learn/courses/30/lessons/284530

AIR_POLLUTION 테이블에서 수원 지역의 연도 별 **평균 미세먼지 오염도**와 **평균 초미세먼지 오염도**를 조회하는 SQL문을 작성해주세요.  
이때, 평균 미세먼지 오염도와 평균 초미세먼지 오염도의 컬럼명은 각각 **PM10, PM2.5**로 해 주시고, 값은 소수 **셋째 자리에서 반올림**해주세요.  
결과는 **연도를 기준으로 오름차순** 정렬해주세요.

```
SELECT YEAR(YM) AS YEAR, ROUND(AVG(PM_VAL1),3) AS PM10, ROUND(AVG(PM_VAL2),3) AS 'PM2.5'
FROM AIR_POLLUTION
WHERE LOCATION2 = '수원'
GROUP BY YEAR
ORDER BY YEAR
```
