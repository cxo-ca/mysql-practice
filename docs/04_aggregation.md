# 04. 데이터 집계

이 문서는 MySQL에서 집계 함수를 사용해 데이터를 요약하고 분석하는 방법을 정리하는 문서입니다.

## 학습 목표

- `COUNT`, `SUM`, `AVG`, `MIN`, `MAX` 집계 함수를 사용할 수 있습니다.
- 전체 데이터 개수, 합계, 평균, 최솟값, 최댓값을 구할 수 있습니다.
- `GROUP BY`를 사용해 그룹별 집계 결과를 만들 수 있습니다.
- `HAVING`을 사용해 그룹화된 결과에 조건을 적용할 수 있습니다.

---

## 집계 함수란?

집계 함수는 여러 행의 데이터를 하나의 요약 결과로 계산하는 함수입니다.

| 함수 | 의미 |
|---|---|
| COUNT | 행 개수 |
| SUM | 합계 |
| AVG | 평균 |
| MIN | 최솟값 |
| MAX | 최댓값 |

---

## COUNT

`COUNT`는 데이터의 개수를 셀 때 사용합니다.

~~~sql
SELECT COUNT(*)
FROM burgers;
~~~

특정 컬럼의 값 개수를 셀 수도 있습니다.

~~~sql
SELECT COUNT(name)
FROM burgers;
~~~

---

## SUM

`SUM`은 숫자 컬럼의 합계를 구할 때 사용합니다.

~~~sql
SELECT SUM(price)
FROM burgers;
~~~

---

## AVG

`AVG`는 숫자 컬럼의 평균을 구할 때 사용합니다.

~~~sql
SELECT AVG(price)
FROM burgers;
~~~

---

## MIN과 MAX

`MIN`은 최솟값, `MAX`는 최댓값을 구할 때 사용합니다.

~~~sql
SELECT MIN(price)
FROM burgers;

SELECT MAX(price)
FROM burgers;
~~~

---

## 별칭 사용

`AS`를 사용하면 조회 결과 컬럼명에 별칭을 붙일 수 있습니다.

~~~sql
SELECT AVG(price) AS avg_price
FROM burgers;
~~~

---

## GROUP BY

`GROUP BY`는 특정 컬럼의 값이 같은 데이터끼리 묶어서 집계할 때 사용합니다.

~~~sql
SELECT protein, COUNT(*) AS burger_count
FROM burgers
GROUP BY protein;
~~~

다른 예시:

~~~sql
SELECT kcal, AVG(price) AS avg_price
FROM burgers
GROUP BY kcal;
~~~

---

## HAVING

`HAVING`은 `GROUP BY`로 묶은 결과에 조건을 걸 때 사용합니다.

~~~sql
SELECT protein, COUNT(*) AS burger_count
FROM burgers
GROUP BY protein
HAVING COUNT(*) >= 2;
~~~

`WHERE`은 그룹화 전의 행에 조건을 걸고, `HAVING`은 그룹화 후의 집계 결과에 조건을 겁니다.

---

## 전체 실습 스크립트

~~~sql
/*********************
 Chapter 04 : 데이터 집계
**********************/

USE mapdonalds;

SELECT *
FROM burgers;

SELECT COUNT(*)
FROM burgers;

SELECT COUNT(name)
FROM burgers;

SELECT SUM(price)
FROM burgers;

SELECT AVG(price)
FROM burgers;

SELECT MIN(price)
FROM burgers;

SELECT MAX(price)
FROM burgers;

SELECT AVG(price) AS avg_price
FROM burgers;

SELECT protein, COUNT(*) AS burger_count
FROM burgers
GROUP BY protein;

SELECT kcal, AVG(price) AS avg_price
FROM burgers
GROUP BY kcal;

SELECT protein, COUNT(*) AS burger_count
FROM burgers
GROUP BY protein
HAVING COUNT(*) >= 2;
~~~

---

## Self Check

`burgers` 테이블을 사용해 집계 함수를 연습합니다.

### 요구 사항

1. 전체 버거 개수를 조회합니다.
2. 전체 버거 가격의 합계를 조회합니다.
3. 평균 가격을 조회합니다.
4. 가장 비싼 버거 가격을 조회합니다.
5. 가장 저렴한 버거 가격을 조회합니다.
6. 단백질 함량별 버거 개수를 조회합니다.
7. 단백질 함량별 버거 개수 중 2개 이상인 그룹만 조회합니다.

### 풀이 스크립트

~~~sql
SELECT COUNT(*) AS total_count
FROM burgers;

SELECT SUM(price) AS total_price
FROM burgers;

SELECT AVG(price) AS avg_price
FROM burgers;

SELECT MAX(price) AS max_price
FROM burgers;

SELECT MIN(price) AS min_price
FROM burgers;

SELECT protein, COUNT(*) AS burger_count
FROM burgers
GROUP BY protein;

SELECT protein, COUNT(*) AS burger_count
FROM burgers
GROUP BY protein
HAVING COUNT(*) >= 2;
~~~

---

## 정리

이 장에서는 여러 데이터를 요약하는 집계 함수와 그룹화 문법을 학습했습니다.

- `COUNT`: 데이터 개수 계산
- `SUM`: 합계 계산
- `AVG`: 평균 계산
- `MIN`: 최솟값 계산
- `MAX`: 최댓값 계산
- `AS`: 결과 컬럼 별칭 지정
- `GROUP BY`: 그룹별 집계
- `HAVING`: 그룹화 결과 조건 적용
