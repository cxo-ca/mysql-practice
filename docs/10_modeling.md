# 10. 데이터 모델링

이 문서는 데이터베이스를 만들기 전에 테이블과 관계를 설계하는 데이터 모델링 개념을 정리하는 문서입니다.

## 데이터 모델링이란?

데이터 모델링은 저장해야 할 데이터를 분석하고, 테이블과 컬럼, 관계를 설계하는 과정입니다.

데이터베이스를 바로 만드는 것이 아니라, 어떤 데이터를 어떤 구조로 저장할지 먼저 정리하는 작업입니다.

---

## 데이터 모델링이 필요한 이유

데이터 모델링을 하면 다음과 같은 장점이 있습니다.

- 중복 데이터를 줄일 수 있습니다.
- 데이터 수정과 관리가 쉬워집니다.
- 테이블 간 관계를 명확하게 만들 수 있습니다.
- 나중에 JOIN과 분석 쿼리를 작성하기 쉬워집니다.

---

## 기본 설계 흐름

데이터 모델링은 보통 다음 순서로 진행합니다.

1. 저장할 데이터 찾기
2. 엔티티 정리하기
3. 컬럼 정리하기
4. Primary Key 정하기
5. 테이블 간 관계 정하기
6. Foreign Key 정하기

---

## 엔티티란?

엔티티는 데이터로 관리할 대상입니다.

예를 들어 학교 시스템에서는 다음과 같은 엔티티가 있을 수 있습니다.

- 학생
- 강의
- 수강
- 교수

각 엔티티는 보통 하나의 테이블이 됩니다.

---

## 컬럼이란?

컬럼은 엔티티가 가지는 속성입니다.

예를 들어 학생 테이블은 다음 컬럼을 가질 수 있습니다.

| 컬럼 | 의미 |
|---|---|
| id | 학생 고유 번호 |
| name | 학생 이름 |
| grade | 학년 |
| major | 전공 |

---

## Primary Key 정하기

Primary Key는 각 행을 구분하는 고유한 값입니다.

학생 테이블에서는 `id`를 Primary Key로 사용할 수 있습니다.

~~~sql
CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    grade INT,
    major VARCHAR(50),
    PRIMARY KEY (id)
);
~~~

---

## 관계 정하기

관계형 데이터베이스에서는 테이블을 나누고, 필요한 경우 관계를 통해 연결합니다.

예를 들어 학생과 수강 정보는 다음처럼 나눌 수 있습니다.

- `students`: 학생 정보
- `courses`: 강의 정보
- `enrollments`: 수강 정보

학생 한 명은 여러 강의를 들을 수 있고, 강의 하나에도 여러 학생이 등록할 수 있습니다.

이런 경우 `enrollments` 테이블을 중간 테이블로 사용합니다.

---

## 예시 테이블 설계

~~~sql
CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    major VARCHAR(50),
    PRIMARY KEY (id)
);

CREATE TABLE courses (
    id INT,
    name VARCHAR(50),
    professor VARCHAR(50),
    PRIMARY KEY (id)
);

CREATE TABLE enrollments (
    id INT,
    student_id INT,
    course_id INT,
    PRIMARY KEY (id),
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (course_id) REFERENCES courses(id)
);
~~~

---

## 정규화란?

정규화는 중복 데이터를 줄이고, 데이터를 더 안정적으로 관리하기 위해 테이블을 나누는 과정입니다.

예를 들어 학생 이름과 강의명을 하나의 테이블에 계속 반복해서 저장하면 중복이 많아집니다.

이를 학생 테이블, 강의 테이블, 수강 테이블로 나누면 데이터 관리가 쉬워집니다.

---

## Self Check

학교 수강 시스템을 기준으로 데이터 모델링을 연습합니다.

### 요구 사항

1. 학생 정보를 저장할 테이블을 설계합니다.
2. 강의 정보를 저장할 테이블을 설계합니다.
3. 수강 정보를 저장할 테이블을 설계합니다.
4. 각 테이블의 Primary Key를 정합니다.
5. 수강 테이블에 Foreign Key를 설정합니다.

### 풀이 스크립트

~~~sql
CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    grade INT,
    major VARCHAR(50),
    PRIMARY KEY (id)
);

CREATE TABLE courses (
    id INT,
    name VARCHAR(50),
    professor VARCHAR(50),
    PRIMARY KEY (id)
);

CREATE TABLE enrollments (
    id INT,
    student_id INT,
    course_id INT,
    PRIMARY KEY (id),
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (course_id) REFERENCES courses(id)
);
~~~

---

## 정리

이 장에서는 데이터베이스를 설계하기 위한 데이터 모델링 개념을 학습했습니다.

- 데이터 모델링은 테이블과 관계를 미리 설계하는 과정입니다.
- 엔티티는 데이터로 관리할 대상입니다.
- 컬럼은 엔티티가 가지는 속성입니다.
- Primary Key는 각 행을 구분하는 고유값입니다.
- Foreign Key는 다른 테이블과 연결하기 위한 참조값입니다.
- 정규화는 중복을 줄이기 위해 테이블을 나누는 과정입니다.
