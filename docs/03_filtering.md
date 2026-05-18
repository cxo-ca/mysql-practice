# 03. 데이터 필터링

이 문서는 MySQL에서 조건을 사용해 원하는 데이터만 조회하는 방법을 정리하는 문서입니다.

## 학습 목표

- `WHERE` 절을 사용해 특정 조건의 데이터를 조회할 수 있습니다.
- 비교 연산자를 사용해 숫자와 문자열 조건을 만들 수 있습니다.
- 논리 연산자를 사용해 여러 조건을 조합할 수 있습니다.
- `BETWEEN`, `IN`, `LIKE`를 사용해 다양한 필터링 조건을 만들 수 있습니다.

---

## WHERE란?

`WHERE`는 전체 데이터 중 조건을 만족하는 행만 조회할 때 사용하는 문법입니다.

~~~sql
SELECT column_name
FROM table_name
WHERE condition;
~~~

예시:

~~~sql
SELECT *
FROM burgers
WHERE price >= 6000;
~~~

---

## 비교 연산자

| 연산자 | 의미 |
|---|---|
| = | 같다 |
| != | 같지 않다 |
| > | 초과 |
| >= | 이상 |
| < | 미만 |
| <= | 이하 |

예시:

~~~sql
SELECT name, price
FROM burgers
WHERE price = 5300;

SELECT name, price
FROM burgers
WHERE price != 5300;

SELECT name, price
FROM burgers
WHERE price >= 6000;
~~~

---

## 논리 연산자

| 연산자 | 의미 |
|---|---|
| AND | 두 조건을 모두 만족 |
| OR | 둘 중 하나 이상 만족 |
| NOT | 조건 부정 |

### AND 예시

~~~sql
SELECT name, price, kcal
FROM burgers
WHERE price >= 6000
AND kcal >= 550;
~~~

### OR 예시

~~~sql
SELECT name, price, protein
FROM burgers
WHERE price >= 7000
OR protein >= 40;
~~~

### NOT 예시

~~~sql
SELECT name, price
FROM burgers
WHERE NOT price >= 6000;
~~~

---

## BETWEEN

`BETWEEN`은 특정 범위 안에 있는 데이터를 조회할 때 사용합니다.

~~~sql
SELECT name, price
FROM burgers
WHERE price BETWEEN 5000 AND 6500;
~~~

위 조건은 `price >= 5000 AND price <= 6500`과 같은 의미입니다.

---

## IN

`IN`은 여러 값 중 하나에 해당하는 데이터를 조회할 때 사용합니다.

~~~sql
SELECT name, price
FROM burgers
WHERE id IN (1, 3, 5);
~~~

위 조건은 `id = 1 OR id = 3 OR id = 5`와 같은 의미입니다.

---

## LIKE

`LIKE`는 문자열 패턴을 기준으로 데이터를 조회할 때 사용합니다.

| 패턴 | 의미 |
|---|---|
| `%문자` | 해당 문자로 끝나는 값 |
| `문자%` | 해당 문자로 시작하는 값 |
| `%문자%` | 해당 문자를 포함하는 값 |

예시:

~~~sql
SELECT name
FROM burgers
WHERE name LIKE '%치즈%';

SELECT name
FROM burgers
WHERE name LIKE '더블%';
~~~

---

## 정렬과 제한

### ORDER BY

`ORDER BY`는 조회 결과를 정렬할 때 사용합니다.

~~~sql
SELECT name, price
FROM burgers
ORDER BY price ASC;
~~~

- `ASC`: 오름차순
- `DESC`: 내림차순

~~~sql
SELECT name, price
FROM burgers
ORDER BY price DESC;
~~~

### LIMIT

`LIMIT`은 조회할 데이터 개수를 제한할 때 사용합니다.

~~~sql
SELECT name, price
FROM burgers
ORDER BY price DESC
LIMIT 3;
~~~

---

## 전체 실습 스크립트

~~~sql
/*********************
 Chapter 03 : 데이터 필터링
**********************/

USE mapdonalds;

SELECT *
FROM burgers;

SELECT name, price
FROM burgers
WHERE price = 5300;

SELECT name, price
FROM burgers
WHERE price != 5300;

SELECT name, price
FROM burgers
WHERE price >= 6000;

SELECT name, price, kcal
FROM burgers
WHERE price >= 6000
AND kcal >= 550;

SELECT name, price, protein
FROM burgers
WHERE price >= 7000
OR protein >= 40;

SELECT name, price
FROM burgers
WHERE NOT price >= 6000;

SELECT name, price
FROM burgers
WHERE price BETWEEN 5000 AND 6500;

SELECT name, price
FROM burgers
WHERE id IN (1, 3, 5);

SELECT name
FROM burgers
WHERE name LIKE '%치즈%';

SELECT name
FROM burgers
WHERE name LIKE '더블%';

SELECT name, price
FROM burgers
ORDER BY price ASC;

SELECT name, price
FROM burgers
ORDER BY price DESC;

SELECT name, price
FROM burgers
ORDER BY price DESC
LIMIT 3;
~~~

---

## Self Check

`burgers` 테이블을 사용해 조건 조회를 연습합니다.

### 요구 사항

1. 가격이 6000원 이상인 버거를 조회합니다.
2. 단백질이 25g 이상인 버거의 이름과 단백질을 조회합니다.
3. 가격이 5000원 이상이고 칼로리가 600kcal 이하인 버거를 조회합니다.
4. 이름에 `치즈`가 들어간 버거를 조회합니다.
5. 가격이 높은 순서대로 상위 3개 버거를 조회합니다.

### 풀이 스크립트

~~~sql
SELECT *
FROM burgers
WHERE price >= 6000;

SELECT name, protein
FROM burgers
WHERE protein >= 25;

SELECT name, price, kcal
FROM burgers
WHERE price >= 5000
AND kcal <= 600;

SELECT *
FROM burgers
WHERE name LIKE '%치즈%';

SELECT name, price
FROM burgers
ORDER BY price DESC
LIMIT 3;
~~~

---

## 정리

이 장에서는 조건을 사용해 필요한 데이터만 조회하는 방법을 학습했습니다.

- `WHERE`: 조건에 맞는 행 조회
- 비교 연산자: 값 비교
- `AND`, `OR`, `NOT`: 조건 조합
- `BETWEEN`: 범위 조건
- `IN`: 여러 값 조건
- `LIKE`: 문자열 패턴 조건
- `ORDER BY`: 정렬
- `LIMIT`: 조회 개수 제한
