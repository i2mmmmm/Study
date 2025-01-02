https://school.programmers.co.kr/learn/courses/30/lessons/157341

CAR_RENTAL_COMPANY_CAR 테이블과 CAR_RENTAL_COMPANY_RENTAL_HISTORY 테이블에서  
**자동차 종류가 세단**인 자동차들 중 **10월에 대여를 시작**한 기록이 있는 **자동차 ID** 리스트를 출력하는 SQL문을 작성해주세요.  
자동차 ID 리스트는 **중복이 없어야** 하며, **자동차 ID를 기준으로 내림차순** 정렬해주세요.

```
SELECT C.CAR_ID
FROM CAR_RENTAL_COMPANY_CAR C
JOIN CAR_RENTAL_COMPANY_RENTAL_HISTORY H ON H.CAR_ID=C.CAR_ID
WHERE C.CAR_TYPE LIKE '세단' AND DATE_FORMAT(H.START_DATE,'%m') = 10
GROUP BY C.CAR_ID
ORDER BY C.CAR_ID DESC
```
