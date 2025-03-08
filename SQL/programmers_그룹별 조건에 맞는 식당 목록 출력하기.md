https://school.programmers.co.kr/learn/courses/30/lessons/131124

MEMBER_PROFILE와 REST_REVIEW 테이블에서 **리뷰를 가장 많이 작성한 회원 1명**의 리뷰들을 조회하는 SQL문을 작성해주세요.  
**회원 이름, 리뷰 텍스트, 리뷰 작성일**이 출력되도록 작성해주시고,  
결과는 **리뷰 작성일을 기준으로 오름차순**, 리뷰 작성일이 같다면 **리뷰 텍스트를 기준으로 오름차순** 정렬해주세요.

```
SELECT M.MEMBER_NAME, R.REVIEW_TEXT,
    DATE_FORMAT(R.REVIEW_DATE, '%Y-%m-%d') AS REVIEW_DATE
FROM MEMBER_PROFILE M RIGHT JOIN REST_REVIEW R
ON M.MEMBER_ID = R.MEMBER_ID
INNER JOIN 
    (SELECT MEMBER_ID, COUNT(MEMBER_ID) AS CNT
    FROM REST_REVIEW
    GROUP BY MEMBER_ID
    ORDER BY CNT DESC LIMIT 1) C
ON M.MEMBER_ID = C.MEMBER_ID
ORDER BY REVIEW_DATE ASC, REVIEW_TEXT ASC
```
