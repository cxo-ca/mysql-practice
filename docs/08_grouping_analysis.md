# 08. 그룹화 분석

이 문서는 GROUP BY와 HAVING을 사용해 데이터를 그룹별로 분석하는 방법을 정리하는 문서입니다.

## GROUP BY란?

GROUP BY는 특정 컬럼의 값이 같은 데이터끼리 묶어서 집계할 때 사용하는 문법입니다.

예를 들어 학과별 학생 수, 카테고리별 평균 가격, 부서별 평균 급여를 구할 때 사용할 수 있습니다.

## 기본 문법

~~~sql
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name;
~~~

## GROUP BY 예시

~~~sql
SELECT major, COUNT(*) AS student_count
FROM students
GROUP BY major;
~~~

## HAVING이란?

HAVING은 GROUP BY로 묶은 결과에 조건을 거는 문법입니다.

WHERE은 그룹화 전의 행에 조건을 걸고, HAVING은 그룹화 후의 집계 결과에 조건을 겁니다.

## HAVING 예시

~~~sql
SELECT major, COUNT(*) AS student_count
FROM students
GROUP BY major
HAVING COUNT(*) >= 2;
~~~

## WHERE와 HAVING 차이

| 구분 | 사용 시점 | 예시 |
|---|---|---|
| WHERE | 그룹화 전 | 특정 학년만 조회 |
| HAVING | 그룹화 후 | 학생 수가 2명 이상인 학과만 조회 |

## 정리

GROUP BY는 데이터를 기준별로 묶고, HAVING은 묶인 결과에 조건을 적용할 때 사용합니다.
