https://school.programmers.co.kr/learn/courses/30/lessons/284527

HR_DEPARTMENT, HR_EMPLOYEES, HR_GRADE 테이블에서 **2022년도 한해 평가 점수가 가장 높은 사원** 정보를 조회하려 합니다.  
2022년도 평가 점수가 가장 높은 사원들의 **점수, 사번, 성명, 직책, 이메일**을 조회하는 SQL문을 작성해주세요.  
2022년도의 평가 점수는 **상,하반기 점수의 합**을 의미하고, 평가 점수를 나타내는 컬럼의 이름은 SCORE로 해주세요.

```
SELECT G.SCORE_SUM AS SCORE, E.EMP_NO, E.EMP_NAME, E.POSITION, E.EMAIL
FROM HR_EMPLOYEES E LEFT JOIN (SELECT EMP_NO, SUM(SCORE) AS SCORE_SUM
                             FROM HR_GRADE
                             WHERE YEAR = 2022
                             GROUP BY EMP_NO
                             ) G
ON E.EMP_NO = G.EMP_NO
ORDER BY SCORE DESC
LIMIT 1
```
