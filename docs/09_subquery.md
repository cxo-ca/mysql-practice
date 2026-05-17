# 09. 서브쿼리

이 문서는 SQL 안에 또 다른 SQL을 넣어 사용하는 서브쿼리 문법을 정리하는 문서입니다.

## 서브쿼리란?

서브쿼리는 하나의 SQL문 안에 포함된 또 다른 SQL문입니다.

복잡한 조건을 한 번에 처리하거나, 다른 조회 결과를 기준으로 데이터를 조회할 때 사용합니다.

## 기본 문법

~~~sql
SELECT column_name
FROM table_name
WHERE column_name = (
    SELECT column_name
    FROM another_table
    WHERE condition
);
~~~

## 예시 1: 평균보다 큰 값 조회

~~~sql
SELECT name, score
FROM students
WHERE score > (
    SELECT AVG(score)
    FROM students
);
~~~

## 예시 2: 특정 조건에 해당하는 ID 조회

~~~sql
SELECT name
FROM students
WHERE id IN (
    SELECT student_id
    FROM enrollments
    WHERE course_name = 'Database'
);
~~~

## 주요 키워드

| 키워드 | 의미 |
|---|---|
| IN | 여러 결과 중 하나라도 일치 |
| NOT IN | 여러 결과 중 일치하지 않음 |
| EXISTS | 서브쿼리 결과가 존재하는지 확인 |
| ANY | 서브쿼리 결과 중 하나라도 조건 만족 |
| ALL | 서브쿼리 결과 전체가 조건 만족 |

## 정리

서브쿼리는 다른 조회 결과를 조건으로 활용할 수 있게 해주는 문법입니다.
복잡한 데이터 조회를 단계적으로 처리할 때 유용합니다.
