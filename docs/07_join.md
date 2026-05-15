# 07. JOIN

이 문서는 여러 테이블의 데이터를 연결해서 조회하는 JOIN 문법을 정리하는 문서입니다.

## JOIN이란?

JOIN은 두 개 이상의 테이블을 공통 컬럼을 기준으로 연결해서 조회하는 문법입니다.

예를 들어 학생 테이블과 수강 테이블이 있을 때, 학생 ID를 기준으로 두 테이블을 연결할 수 있습니다.

## 기본 문법

~~~sql
SELECT column_name
FROM table_a
JOIN table_b
ON table_a.key = table_b.key;
~~~

## INNER JOIN

INNER JOIN은 두 테이블에서 조건이 일치하는 데이터만 조회합니다.

~~~sql
SELECT students.name, enrollments.course_name
FROM students
INNER JOIN enrollments
ON students.id = enrollments.student_id;
~~~

## LEFT JOIN

LEFT JOIN은 왼쪽 테이블의 데이터는 모두 조회하고, 오른쪽 테이블은 조건이 일치하는 데이터만 연결합니다.

~~~sql
SELECT students.name, enrollments.course_name
FROM students
LEFT JOIN enrollments
ON students.id = enrollments.student_id;
~~~

## 정리

JOIN은 테이블을 나누어 관리하면서도 필요한 순간에 데이터를 연결해서 조회할 수 있게 해주는 핵심 문법입니다.
