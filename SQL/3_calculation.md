### 1. 사칙연산
- +, -, *, /
- %, MOD  = 나눈 나머지

- SELECT 5-2;  
  이렇게 하면 데이터 뿐 아니라 **열이름도 3** 인데  
- SELECT 5-2 AS DIFFERENCE;  
  이렇게 하면 데이터만 3이고 **열이름은 DIFFERENCE**가 된다

- SELECT 3*(12-2)/2 AS NUMBER, 'HELLO' AS TEXT;

- SELECT 'ABC' + 3 ;  
  -> JAVA 는 ABC3 으로 나오지만  MySQL의 경우 그냥 **3으로 출력** (문자열 + 숫자 = 숫자)  
- SELECT 'ABC' * 3 ;  
  **결과값 = 0**
- SELECT '1' + '002' * 3 ;  
  이렇게 숫자로 구성된 문자열도 자동으로 숫자로 인식해서 **결과값은 7**
- SELECT ORDER_ID + PRODUCT_ID FROM ORDER_DETAILS;  
  이렇게 하면 두 아이디의 값이 더해진 값이 나옴

### 2. 참/거짓 연산

- SELECT TRUE, FALSE;  
  TRUE 　FALSE  
  1 　　　0
- SELECT !TRUE, NOT 1, !FALSE, NOT FALSE;  
  **!는 반대**를 의미/ 결과값은 **0 0 1 1** 이 나옴

- SELECT 0=TRUE, 1=TRUE, 0=FALSE, 1=FALSE;  
  결과값 ; **0 1 1 0**

- IS = 양쪽의 결과가 TRUE, FALSE 로 같은 결과일 때  
  IS NOT = 양쪽 결과 다를 때  
  AND, && = 양쪽 TRUE 일 때  
  OR, || = 한쪽 TRUE 일 때

- 비교연산자  
  = : 양쪽 값이 같음  
  !=, <> : 양쪽 값이 다름  
  \>, < : 값이 한쪽이 큼  
  \>=, <= : 값이 같거나 한쪽이 큼

- SELECT 'A' < 'B'; 결과가 1로 나오는 이것은 **참**
  (알파벳도 순서에 따라 크기를 매김, **늦게 나오는 알파벳이 큰 것**)  
  SELECT 'A' = 'a'; **참** -> 대소문자 구분을 하지 않음

- SELECT PRODUCT_NAME, PRICE, PRICE > 20 AS EXPENSIVE FROM PRODUCTS;  
  SELECT PRODUCT_NAME, PRICE, NOT PRICE > 20 AS CHAEP FROM PRODUCTS;
--------------------------
- BETWEEN {MIN} AND {MAX} 두 값 사이에 있다

- SELECT 5 BETWEEN 1 AND 10; **참**  
  SELECT 5 BETWEEN 10 AND 1; **거짓** (**작은 숫자부터** 시작해야 함)

- SELECT 'BANANA' BETWEEN 'APPLE' AND 'CAMERA' ; **참**
  알파벳 따라감 첫글자 B 가 A 와 C 사이에 있기에 참

- SELECT * FROM CUSTOMERS  
  WHERE CUSTOMER_NAME BETWEEN 'b' AND 'c' ;  
  B와 C 사이의 이름만 오도록 결국 **B로 시작하는 이름**만 올 수 있음  
  더 효율적인 걸 배우겠지만 일단은 여기까지

- IN(...) 선택지 안에 있는가  
  SELECT 3-1 IN (1,2,3,4) 결과 -> **참**  
  SELECT 3-1 NOT IN (1,2,3,4) 결과 -> **거짓**

- LIKE'...%...' 0~N개 문자를 가진 패턴  
  LIKE'..._...' _갯수만큼의 문자를 가진 패턴

- SELECT 'HELLO' LIKE 'HEL%'; -> **참**  
  SELECT 'HELLO' LIKE 'H%O'; -> **참**  
  SELECT 'HELLO' LIKE '%H'; -> **거짓** (H 로 끝나는 단어는 아니기 때문에)  
  SELECT 'HELLO' LIKE '%HELLO%'; -> **참**  
  % 는 **0개의 문자가 온다**도 포함이라 뭐가 안와도 된다.


- 아까 B로 시작하는 더 효율적인 거  
  SELECT * FROM CUSTOMERS
  WHERE CUSTOMER_NAME LIKE 'B%' ;

- % 가 몇개든 상관없는 것이라면 \_는 딱 한개와 치환되는 것  
  SELECT 'HELLO' LIKE 'HEL_'; -> **거짓**  
  SELECT 'HELLO' LIKE 'HELL_'; -> **참**  
  SELECT 'HELLO' LIKE '_HELLO'; -> **거짓**

- SELECT * FROM EMPLOYEES  
  WHERE NOTES LIKE '%economics%';  
  economics 라는 단어가 들어있는 모든 걸 찾겠다








![image](https://github.com/user-attachments/assets/97c61b16-f52a-4dfd-ae97-c2d28823a6ae)
