### 1. 숫자형 함수  
ROUND 반올림  
CEIL 올림  
FLOOR 내림  
ABS 절대값    
GREATEST (괄호 안에서) 가장 큰 값  
LEAST (괄호 안에서) 가장 작은 값  
MAX 최댓값  
MIN 최솟값  
COUNT 갯수(NULL값 빼고)  
SUM 총 합  
AVG 평균  
POW(A,B) = POWER(A,B) A를 B만큼 제곱  
SQRT 제곱근  
　　SQRT(16) = POWER(16, 1/2)  
TRUNCATE(A,n) A를 소수점 n번째 자리까지 선택   
　　TRUNCATE(1234.5678, 1) = 1234.5  
  　TRUNCATE(1234.5678, 0) = 1234  
　　TRUNCATE(1234.5678, -1) = 1230  

### 2. 문자열 함수  
UPPER = UCASE 모두 대문자로  
LOWER = LCASE 모두 소문자로  
CONCAT(... , ... , ... ) 모든 글자 이어붙임  
CONCAT_WS(s, ...) 모든 글자 s로 이어붙임  
　　SELECT CONCAT_WS('-' , 2021, 8, 15, 'AM')  
　　　2021-8-15-AM  
SUBSTR = SUBSTRING 주어진 값에 따라 문자열 자름  
　　SUBSTR('ABCDEFG', 3)  
　　　CDEFG  
　　SUBSTR('ABCDEFG', 3,2)  
　　　CD  
　　SUBSTR('ABCDEFG', -3)  
　　　EFG  
　　SUBSTR('ABCDEFG', -3,2)  
　　　EF  
LEFT 왼쪽부터 n개 글자  
RIGHT 오른쪽부터 n개 글자  
LENGTH 문자열의 바이트 길이  
CHAR_LENGTH = CHARACTER_LENGTH 문자열의 문자 길이  
　　LENGTH('안녕') = 6  
　　CHAR_LENGTH('안녕') = 2  
TRIM 양쪽 공백 제거  
LTRIM 왼쪽 공백 제거  
RTRIM 오른쪽 공백 제거  
LPAD(S,N,P) S 가 N개 글자가 될 때까지 P 를 왼쪽에 이어붙임  
RPAD(S,N,P) S 가 N개 글자가 될 때까지 P 를 오른쪽에 이어붙임  
　　1,2,3,4, 이런 열을 LPAD 써서 001, 002, 003, 004 이렇게 바꿔서 총 글자 갯수를 맞춰줄 수 있음  
REPLACE(S,A,B) S 중 A 를 B 로 변경  
INSTR(S,s) S중 s의 첫 위치 반환, 없을 시 0  
CAST(A,T) A를 T 자료형으로 변환  
