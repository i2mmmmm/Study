
CURRENT_DATE, CURDATE : 현재 날짜 반환  
CURRENT_TIME, CURTIME : 현재 시간 반환  
CURRENT_TIMESTAMP, NOW : 현재 시간과 날짜 반환  

SELECT CURDATE(), CURTIME(), NOW()  

SELECT  
　　'2021-6-1' = '2021-06-01',　　　　　　　-> FALSE  
　　DATE('2021-6-1') = DATE('2021-06-01'),　-> TRUE  
　　'1:2:3' = '01:02:03',　　　　　　　　　　-> FALSE  
　　TIME('1:2:3') = TIME('01:02:03')　　　　　->TRUE  

YEAR : 주어진 DATETIME 값의 년도 반환  
MONTHNAME : 주어진 DATETIME 값의 월(영문) 반환  
MONTH : 주어진 DATETIME 값의 월 반환  
WEEKDAY : 주어진 DATETIME 값의 요일값 반환(월요일 : 0)  
DAYNAME : 주어진 DATETIME 값의 요일명 반환  
DAYOFMONTH, DAY : 주어진 DATETIME 값의 날짜(일) 반환  


HOUR : 시 반환  
MINUTE : 분 반환  
SECOND : 초 반환
