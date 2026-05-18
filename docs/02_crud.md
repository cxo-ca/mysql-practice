# 02. 데이터 CRUD

이 문서는 MySQL에서 데이터베이스와 테이블을 만들고, 데이터를 생성·조회·수정·삭제하는 CRUD 문법을 정리하는 문서입니다.

## 학습 목표

- 데이터베이스를 생성하고 선택할 수 있습니다.
- 테이블을 생성하고 구조를 확인할 수 있습니다.
- 데이터를 삽입, 조회, 수정, 삭제할 수 있습니다.
- 기본키를 기준으로 특정 데이터를 안전하게 수정하거나 삭제할 수 있습니다.

---

## CRUD란?

CRUD는 데이터 처리의 기본 동작을 의미합니다.

| 구분 | 의미 | SQL |
|---|---|---|
| Create | 데이터 생성 | INSERT |
| Read | 데이터 조회 | SELECT |
| Update | 데이터 수정 | UPDATE |
| Delete | 데이터 삭제 | DELETE |

---

## 데이터베이스 생성과 선택

~~~sql
SHOW DATABASES;

CREATE DATABASE mapdonalds;

USE mapdonalds;

SELECT DATABASE();
~~~

## 데이터베이스 삭제

~~~sql
DROP DATABASE mapdonalds;
~~~

데이터베이스를 삭제하면 내부 테이블과 데이터도 함께 삭제되므로 주의해야 합니다.

---

## 테이블 생성

~~~sql
CREATE TABLE burgers (
    id INTEGER,
    name VARCHAR(50),
    price INTEGER,
    gram INTEGER,
    kcal INTEGER,
    protein INTEGER,
    PRIMARY KEY(id)
);
~~~

## 테이블 구조 확인

~~~sql
DESC burgers;
~~~

---

## 데이터 삽입

### 단일 데이터 삽입

~~~sql
INSERT INTO burgers(id, name, price, gram, kcal, protein)
VALUES(1, '빅맨', 5300, 223, 583, 27);
~~~

### 다중 데이터 삽입

~~~sql
INSERT INTO burgers(id, name, price, gram, kcal, protein)
VALUES
    (2, '베이컨 틈메이러 디럭스', 6200, 242, 545, 27),
    (3, '맨스파이시 상해 버거', 5300, 235, 494, 20),
    (4, '슈비두밥 버거', 6200, 269, 563, 21),
    (5, '더블 쿼터파운드 치즈', 7700, 275, 770, 50);
~~~

---

## 데이터 조회

### 전체 컬럼 조회

~~~sql
SELECT *
FROM burgers;
~~~

### 특정 컬럼 조회

~~~sql
SELECT name, price
FROM burgers;
~~~

---

## 데이터 수정

### 전체 데이터 수정

~~~sql
UPDATE burgers
SET price = 1000;
~~~

전체 데이터를 수정하면 모든 행이 바뀌므로 실습 외에는 주의해야 합니다.

### 안전 모드 해제와 설정

~~~sql
SET SQL_SAFE_UPDATES = 0;
~~~

- `0`: 안전 모드 해제
- `1`: 안전 모드 설정

### 특정 데이터 수정

~~~sql
UPDATE burgers
SET price = 500
WHERE id = 1;
~~~

특정 데이터를 수정할 때는 `WHERE` 조건을 반드시 작성해야 합니다.

---

## 데이터 삭제

~~~sql
DELETE FROM burgers
WHERE id = 4;
~~~

특정 데이터를 삭제할 때도 `WHERE` 조건을 반드시 작성해야 합니다.

---

## 테이블 삭제

~~~sql
DROP TABLE burgers;
~~~

테이블을 삭제하면 테이블 구조와 데이터가 모두 삭제됩니다.

---

## 전체 실습 스크립트

~~~sql
/*********************
 Chapter 02 : 데이터 CRUD
**********************/

SHOW DATABASES;

CREATE DATABASE mapdonalds;

USE mapdonalds;

SELECT DATABASE();

CREATE TABLE burgers (
    id INTEGER,
    name VARCHAR(50),
    price INTEGER,
    gram INTEGER,
    kcal INTEGER,
    protein INTEGER,
    PRIMARY KEY(id)
);

DESC burgers;

INSERT INTO burgers(id, name, price, gram, kcal, protein)
VALUES(1, '빅맨', 5300, 223, 583, 27);

SELECT *
FROM burgers;

INSERT INTO burgers(id, name, price, gram, kcal, protein)
VALUES
    (2, '베이컨 틈메이러 디럭스', 6200, 242, 545, 27),
    (3, '맨스파이시 상해 버거', 5300, 235, 494, 20),
    (4, '슈비두밥 버거', 6200, 269, 563, 21),
    (5, '더블 쿼터파운드 치즈', 7700, 275, 770, 50);

SELECT name, price
FROM burgers;

SET SQL_SAFE_UPDATES = 0;

UPDATE burgers
SET price = 1000;

SELECT *
FROM burgers;

UPDATE burgers
SET price = 500
WHERE id = 1;

DELETE FROM burgers
WHERE id = 4;

SELECT *
FROM burgers;
~~~

---

## Self Check

`starbuuks` 데이터베이스를 사용해서 CRUD를 한 번 더 연습합니다.

### 요구 사항

1. `starbuuks` 데이터베이스를 생성하고 진입합니다.
2. `coffees` 테이블을 생성합니다.
3. 컬럼은 `id`, `name`, `price`로 구성합니다.
4. 커피 5종 데이터를 한 번에 삽입합니다.
5. 모든 커피 이름을 조회합니다.
6. 카푸치노 가격을 200원 인상합니다.
7. 콜드브루 데이터를 삭제합니다.
8. 최종 커피 데이터를 전체 조회합니다.

### 풀이 스크립트

~~~sql
CREATE DATABASE starbuuks;

USE starbuuks;

SELECT DATABASE();

CREATE TABLE coffees (
    id INTEGER,
    name VARCHAR(50),
    price INTEGER,
    PRIMARY KEY(id)
);

DESC coffees;

INSERT INTO coffees(id, name, price)
VALUES
    (1, '아메리카노', 3800),
    (2, '카페라떼', 4000),
    (3, '콜드브루', 3500),
    (4, '카페모카', 4500),
    (5, '카푸치노', 5000);

SELECT name
FROM coffees;

UPDATE coffees
SET price = price + 200
WHERE id = 5;

DELETE FROM coffees
WHERE id = 3;

SELECT *
FROM coffees;
~~~

---

## 정리

이 장에서는 MySQL의 가장 기본적인 데이터 처리 흐름을 학습했습니다.

- `CREATE DATABASE`: 데이터베이스 생성
- `USE`: 사용할 데이터베이스 선택
- `CREATE TABLE`: 테이블 생성
- `INSERT`: 데이터 삽입
- `SELECT`: 데이터 조회
- `UPDATE`: 데이터 수정
- `DELETE`: 데이터 삭제
- `DROP TABLE`: 테이블 삭제
