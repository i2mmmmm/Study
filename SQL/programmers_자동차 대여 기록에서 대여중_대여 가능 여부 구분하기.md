https://school.programmers.co.kr/learn/courses/30/lessons/157340


CAR_RENTAL_COMPANY_RENTAL_HISTORY 테이블에서  
**2022년 10월 16일에 대여 중**인 자동차인 경우 **'대여중'** 이라고 표시하고,  
대여 중이지 않은 자동차인 경우 **'대여 가능'**을 표시하는 컬럼 (**컬럼명: AVAILABILITY**)을 추가하여  
자동차 **ID와 AVAILABILITY** 리스트를 출력하는 SQL문을 작성해주세요.  
이때 반납 날짜가 2022년 10월 16일인 경우에도 '대여중'으로 표시해주시고  
결과는 **자동차 ID**를 기준으로 **내림차순** 정렬해주세요.  

```
SELECT CAR_ID, IF(AVAI = 1,'대여중','대여 가능') AS AVAILABILITY
FROM (SELECT CAR_ID, SUM(IF(START_DATE <= '2022-10-16' AND END_DATE >= '2022-10-16',1,0)) AS AVAI
      FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
      GROUP BY CAR_ID) AS RENT
ORDER BY CAR_ID DESC
```
