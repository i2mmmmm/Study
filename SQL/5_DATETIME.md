### 1. 시간/날짜 함수
CURRENT_DATE, CURDATE : 현재 날짜 반환  
CURRENT_TIME, CURTIME : 현재 시간 반환  
CURRENT_TIMESTAMP, NOW : 현재 시간과 날짜 반환  

SELECT CURDATE(), CURTIME(), NOW()  

```
SELECT  
　　'2021-6-1' = '2021-06-01',　　　　　　　-> FALSE  
　　DATE('2021-6-1') = DATE('2021-06-01'),　-> TRUE  
　　'1:2:3' = '01:02:03',　　　　　　　　　　-> FALSE  
　　TIME('1:2:3') = TIME('01:02:03')　　　　　->TRUE  
```

YEAR : 주어진 DATETIME 값의 년도 반환  
MONTHNAME : 주어진 DATETIME 값의 월(영문) 반환  
MONTH : 주어진 DATETIME 값의 월 반환  
WEEKDAY : 주어진 DATETIME 값의 요일값 반환(월요일 : 0)  
DAYNAME : 주어진 DATETIME 값의 요일명 반환  
DAYOFMONTH, DAY : 주어진 DATETIME 값의 날짜(일) 반환  


HOUR : 시 반환  
MINUTE : 분 반환  
SECOND : 초 반환

ADDDATE, DATE_ADD : 시간/날짜 더하기  
SUBDATE, DATE_SUB : 시간/날짜 빼기  

```
SELECT
　　ADDDATE('2024-11-26', INTERVAL 1 YEAR),
　　ADDDATE('2024-11-26', INTERVAL -2 MONTH),
　　ADDDATE('2024-11-26', INTERVAL 3 WEEK),
　　ADDDATE('2024-11-26', INTERVAL -5 MINUTE),　　->전날 23시 55분
```
DATE_DIFF : 두 시간/ 날짜 간 일수 차  
TIME_DIFF : 두 시간/ 날짜 간 시간 차

DATEDIFF(NOW(), '2023-11-26')　　　-> 365  
DATEDIFF('2023-11-26', NOW())　　　-> -365

LAST_DAY : 주어진 날짜 그 달의 마지막 날

DATE_FORMAT : 시간, 날짜를 지정한 형식으로 반환  
%Y : 년도 4자리  
%y : 년도 2자리  
%M : 월 영문  
%m : 월 숫자  
%D : 일 영문(1st, 2nd, 3rd, ...)  
%d, %e : 일 숫자 (01~31)  
%T : hh:mm:ss  
%r : hh:mm:ss AM/PM  
%H, %k : 시 (~23)  
%h, %l : 시 (~12)  
%i : 분  
%S, %s : 초  
%p : AM/PM  

ex)
```
SELECT  
　　DATE_FORMAT( NOW(), '%y-%m-%d %h:%i:%s %p'),  
　　DATE_FORMAT( NOW(), '%Y년 %m월 %d일 %p %h시 %i분 %s초');  
```
원하는 형식으로 만들기  
```
REPLACE(  
REPLACE(  
　DATE_FORMAT( NOW(), '%Y년 %m월 %d일 %p %h시 %i분 %s초'),  
　'AM', '오전'  
),  
'PM', '오후') 이렇게 AM, PM 을 오전, 오후로 바꿀 수도 있다  
```



### 2. 기타 함수들  
IF(조건, T, F) : 조건이 참이라면 T값, 거짓이면 F값 반환  

이보다 복잡한 조건은 CASE 문을 사용  
```
CASE  
　WHEN -1 > 0 THEN '-1은 양수',  
　WHEN -1 = 0 THEN '-1은 0',  
　ELSE '-1은 음수'  
END;  
```
IFNULL(A, B) : A가 NULL이면 B 출력  
