# 05. 자료형

이 문서는 MySQL에서 사용하는 주요 자료형을 정리하는 문서입니다.

## 자료형이란?

자료형은 컬럼에 어떤 종류의 데이터를 저장할지 정하는 규칙입니다.

## 주요 자료형

| 구분 | 자료형 | 설명 |
|---|---|---|
| 숫자형 | INT | 정수 저장 |
| 숫자형 | FLOAT | 실수 저장 |
| 문자형 | CHAR | 고정 길이 문자열 저장 |
| 문자형 | VARCHAR | 가변 길이 문자열 저장 |
| 날짜형 | DATE | 날짜 저장 |
| 날짜형 | DATETIME | 날짜와 시간 저장 |

## 예시

```sql
CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    birth_date DATE,
    score FLOAT
);
