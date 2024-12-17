### 1. 비상관 서브쿼리
```
SELECT CATEGORY_ID, CATEGORY_NAME, DESCRIPTION,
　　( SELECT PRODUCT_NAME FROM PRODUCTS WHERE PRODUCT_ID =1 )
FROM CATEGORIES;
```
```
SELECT * FROM PRODUCTS
WHERE PRICE <  (SELECT AVG(PRICE) FROM PRODUCTS);
```
```
SELECT CATEGORY_ID, CATEGORY_NAME, DESCRIPTION
FROM CATEGORIES
WHERE CATEGORY_ID IN (SELECT CATEGORYID FROM PRODUCTS WHERE PRICE>50);
```
서브쿼리를 SELECT 나 WHERE 문 뒤에 쓰는 것

~ALL : 서브쿼리의 모든 결과에 대해 ~하다  
~ANY : 서브쿼리의 하나 이상의 결과에 대해 ~하다

```
SELECT * FROM PRODUCTS 
WHERE PRICE > ALL (SELECT PRICE FROM PRODUCTS WHERE CATEGORY_ID =2);
```
```
SELECT MAX(PRICE) FROM PRODUCTS
WHERE CATEGORY_ID = 2
```
위의 두 쿼리는 같은 결과

비상관쿼리 : 괄호 안의 쿼리와 바깥 쿼리가 독자적으로 실행되는 서브쿼리문

### 2. 상관 서브쿼리

괄호 안의 쿼리와 바깥 쿼리가 맞물려져서 돌아가는 서브쿼리문

```
SELECT PRODUCT_ID, PRODUCT_NAME, 
(SELECT CATEGORY_NAME FROM CATEGORIES C
　WHERE C.CATEGORY_ID = P.CATEGORI_ID)
AS CATEGORY_NAME
FROM PRODUCTS P;
```

제품 ID, 제품 이름, 카테고리 이름 을 가져오는데  
그 중 카테고리 이름은  
카테고리 테이블과 제품 테이블 두 곳에서 카테고리 ID 가 일치하는 것만 가져오기

```
SELECT
SupplierName, Country, City,
(
　　SELECT COUNT(*) FROM Customers C
　　WHERE C.Country = S.Country
) AS CustomersInTheCountry,
(
　　SELECT COUNT(*) FROM Customers C
　　WHERE C.Country = S.Country
　　　And C.City = S.City
) AS CustomersInTheCity
FROM Suppliers S;
```



```SELECT
　productID, productNAME, categoryID, price
FROM products P1
WHERE price < (
	SELECT AVG(price) FROM products P2
	WHERE P2.categoryID = P1.categoryID
);
```
같은 테이블을 두번 가져옴  
해당 카테고리의 평균보다 가격이 낮은 것만 가져오겠다.

**EXISTS/ NOT EXISTS**  
존재하는가 존재하지 않는가
```
SELECT categoryID, categoryNAME
FROM categories C
WHERE EXISTS (
　SELECT * FROM products P
　WHERE P.categoryID = C.categoryID
　AND P.price>80
)
```
가격이 80이 넘는 것이 존재한다면 가져오기
