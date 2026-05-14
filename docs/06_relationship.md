# 06. 관계 만들기

이 문서는 관계형 데이터베이스에서 테이블 간 관계를 만드는 방법을 정리하는 문서입니다.

## 관계란?

관계는 하나의 테이블이 다른 테이블과 연결되는 구조입니다.

예를 들어 학생 테이블과 수강 테이블은 학생 ID를 기준으로 연결할 수 있습니다.

## Primary Key

Primary Key는 테이블에서 각 행을 구분하는 고유한 값입니다.

~~~sql
CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    PRIMARY KEY (id)
);
~~~

## Foreign Key

Foreign Key는 다른 테이블의 Primary Key를 참조하는 값입니다.

~~~sql
CREATE TABLE enrollments (
    id INT,
    student_id INT,
    course_name VARCHAR(50),
    PRIMARY KEY (id),
    FOREIGN KEY (student_id) REFERENCES students(id)
);
~~~

## 정리

관계형 데이터베이스에서는 Primary Key와 Foreign Key를 사용해 테이블 사이의 연결을 만듭니다.
