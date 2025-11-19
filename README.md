# MySQL 강의 실습 정리

MySQL Workbench를 사용해서 강의 실습한 내용을 정리한 레포지토리입니다.

## Chapter 02: 데이터 CRUD

파일: `chapter02_crud.sql`

포함 내용:

- 데이터베이스 생성/삭제
  - `SHOW DATABASES;`
  - `CREATE DATABASE mapdonalds;`
  - `USE mapdonalds;`
  - `DROP DATABASE mapdonalds;`

- 테이블 생성
  - `CREATE TABLE burgers (...)`

- 데이터 삽입 (INSERT)
  - 단일 데이터 삽입
  - 다중 데이터 삽입

- 데이터 조회 (SELECT)
  - 전체 컬럼 조회
  - 특정 컬럼(name, price) 조회

- 데이터 수정 (UPDATE)
  - 전체 price 변경
  - 특정 id(기본키)를 이용한 가격 변경

- 데이터 삭제 (DELETE)
  - 특정 id의 레코드 삭제

- 테이블 삭제 (DROP TABLE)
  - `DROP TABLE burgers;`


/*********************
Chapter 02 : 데이터 CRUD
**********************/
SHOW DATABASES;				-- DB 목록 조회
CREATE DATABASE mapdonalds; -- DB 생성
USE mapdonalds;				-- DB 진입
SELECT DATABASE();			-- 현재 사용중인 DB
DROP DATABASE mapdonalds;	-- DB 삭제

-- 테이블 생성
CREATE TABLE burgers(
    id      INTEGER,
    name    VARCHAR(50),
    price   INTEGER,
    gram    INTEGER,
    kcal    INTEGER,
    protein INTEGER,
    PRIMARY KEY(id)
);

-- 테이블 구조 조회
DESC burgers;

-- 단일 데이터 삽입
INSERT INTO burgers(id, name, price, gram, kcal, protein)
VALUES(1, '빅맨', 5300, 223, 583, 27);

-- 데이터 조회
SELECT *	 -- 모든 컬럼을 조회
FROM burgers; -- 버거 테이블에서

-- 다중 데이터 삽입
INSERT INTO
    burgers(id, name, price, gram, kcal, protein)
VALUES
    (2, '베이컨 틈메이러 디럭스', 6200, 242, 545, 27),
    (3, '맨스파이시 상해 버거', 5300, 235, 494, 20),
    (4, '슈비두밥 버거', 6200, 269, 563, 21),
    (5, '더블 쿼터파운드 치즈', 7700, 275, 770, 50);

-- 데이터 조회
SELECT name, price	-- 이름, 가격 컬럼을 조회
FROM burgers; 		-- 버거 테이블에서

-- 데이터 수정
UPDATE burgers
SET price = 1000;

-- 안전모드 해제/설정
SET SQL_SAFE_UPDATES = 0; -- 0 : 해제, 1 : 설정

-- 전체 버거 조회
SELECT * FROM burgers;

-- 빅맨 버거만 500원으로 변경
UPDATE burgers
SET price = 500
WHERE id = 1; -- 특정 대상값 변경시, 조건은 반드시 기본키를 사용

-- id가 4인 버거를 삭제
DELETE FROM burgers
WHERE id = 4;

-- 전체 테이블 삭제: burgers
DROP TABLE burgers;
DESC burgers;
SELECT * FROM burgers;
