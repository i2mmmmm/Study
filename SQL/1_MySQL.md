## MySQL 강의
### 1. RDBMS 란? MySQL이란?
- Database
- DBMS(Database Management System) 데이터베이스 관리 시스템
- **SQL**(Structured Query Language) SQL으로 데이베이스의 정보를 관리
  - C, java, python 처럼 다양한 활용이 가능한 범용 프로그래밍 언어라기보다는 HTML처럼 특정 사용처에서 쓰이는 **도메인 특화 언어**
  - 엑셀의 표와 닮은 테이블을 만들어서 데이터 베이스라는 상자 안에 정보들을 담아 사용자가 원하는대로 정보를 넣고 빼고 읽어올 수 있게 해주는 **관계형 데이터베이스 관리 시스템(RDBMS)**
  - 중복되는 행이 많으면 **테이블을 분리**해서 **효율적**으로 관리 -> **관계형**  
    고유 id 를 각 테이블에 넣어줘서 연결시켜주기 (-> JOIN을 사용해서 연결해서 볼 수 있음)
  - 데이터를 다양한 방식으로 필터링, 정렬, 가공해서 내가 원하는 **의미있는 정보**로 만들어내는 관계형 데이터베이스
  - RDBMS 예시 -> MySQL, Oracle, MS SQL, PostgreSQL 등등
    비관계형 예시 - MongoDB Cassandra, DinamoDB, Riak, Redis 등등 (NOSQL 데이터베이스)
