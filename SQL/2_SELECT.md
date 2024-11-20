SQL 연습공간 : https://www.w3schools.com/mysql/trymysql.asp?filename=trysql_select_all

1. 조회 기능 (**SELECT**)  
- **모든** 컬럼 조회  
SELECT * FROM Customers;  
**--** 주석 달기  
- 원하는 컬럼만 가져오기  
SELECT CustomerName FROM Customers;  
- 여러 컬럼 가져오기
SELECT CustomerName, Contact, Country FROM Customers;  
- 컬럼, 숫자, 문자열, null 값 만들어서 가져오기
SELECT CustomerName, 1, 'Hello', NULL FROM Customers;  

2. 원하는 행(row) 가져오기 (**WHERE**)    
SELECT * FROM Orders **WHERE** EmployeeID = 3;    
SELECT 이런 지시어들은 대문자이건 소문자이건 상관없으나 SQL에서는 대부분 가독성좋게 대문자를 쓰는 편

3. 원하는 순서 (**ORDER BY**)  
SELECT * FROM OrderDetails  
ORDER BY ProductID ASC, Quantity DESC; ( 이 경우 순서대로 진행 ProductID 오름차순하고 Quantity 내림차순 하고 출력 )  
**ASC : 오름차순 (기본)  
DESC : 내림차순**  


4. 원하는 양 (**LIMIT**)    
SELECT * FROM OrderDetails  
**LIMIT 30**;  
여기에서 LIMIT 10, 30 이렇게 쓰면 첫페이지는 10개 두번째 페이지는 30개

5. 열이름 변경 (**AS**)  
SELECT ProductID **AS** '아이디' FROM OrderDetails;
