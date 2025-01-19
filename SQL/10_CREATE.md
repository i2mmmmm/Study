### 1. 테이블 만들기 - CREATE TABLE

```
CREATE TABLE PEOPLE (
	ID INT,
	NAME VARCHAR(10),
	AGE TINYINT,
	BIRTHDAY DATE
);
```

### 2. 테이블 변경 - ALTER TABLE

```
ALTER TABLE PEOPLE RENAME TO FRIENDS,    # 테이블 이름 변경
CHANGE COLUMN ID ID TINYINT,             # 컬럼 자료형 변경
CHANGE COLUMN NAME NICKNAME VARCHAR(10), # 컬럼 이름 변경
DROP COLUMN BIRTHDAY,                    # 컬럼 삭제
ADD COLUMN MARRIED TINYINT AFTER AGE;    # 컬럼 추가

DROP TABLE FRIENDS; # 테이블 삭제
```

### 3. 테이블에 데이터 넣기 INSERT INTO

```
INSERT INTO PEOPLE
	(ID, NAME, AGE, BIRTHDAY)
	VALUES(1, '하니', 20, '2005-01-01');

- 모든 컬럼에 값을 넣을 때는 컬럼명 생략 가능
INSERT INTO PEOPLE
	VALUES(2, '민지', 20, '2005-02-02');

- 일부 컬럼에만 값 넣기 (안넣은 값 NULL이 됨)
INSERT INTO PEOPLE
	(ID, NAME, BIRTHDAY)
	VALUES(3, '다니엘', '2005-03-03');

- 자료형이 맞지 않으면 오류 발생
INSERT INTO PEOPLE
	(ID, NAME, AGE, BIRTHDAY)
	VALUES(1, '제니', '스물둘', '2003-01-01');

- 여러 행을 한번에 입력
INSERT INTO PEOPLE
	(ID, NAME, AGE, BIRTHDAY)
	VALUES
		(4, '해린', 18, '2007-01-01'),
		(5, '혜인', 18, '2007-02-02');
```

### 4. 테이블 생성시 제약을 넣기

```
CREATE TABLE PEOPLE(
	ID INT AUTO_INCREMENT PRIMARY KEY,
	NAME VARCHAR(10) NOT NULL,
	NICKNAME VARCHAR(10) UNIQUE NOT NULL,
	AGE TINYINT UNSIGNED,
	MARRIED TINYINT DEFAULT 0
);
```

AUTO_INCREMENT : 새 행 생성시마다 자동으로 1씩 증가 (값을 넣어줄 필요없이 자동으로)  
PRIMARY KEY : 중복 입력 불가, NULL(빈 값)을 넣을 수 없음  
UNIQUE : 중복 입력 불가, NULL은 가능  
UNSIGNED : (숫자) 양수만 가능  
DEFAULT : 값 입력 없을 시 기본값 설정

**PRIMARY KEY (기본키)**
- 테이블마다 하나만 가능
- 기본적으로 인덱스 생성 (기본키 행 기준으로 **빠른 검색** 가능)
- 보통 AUTO_INCREMENT와 함께 사용
- 각 행을 고유하게 **식별** 가능 -> 테이블마다 **하나씩** 둘 것
