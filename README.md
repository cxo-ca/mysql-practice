# MySQL Practice

MySQL 입문 강의를 들으며 SQL 기본 문법과 데이터베이스 개념을 정리한 실습 저장소입니다.

이 저장소는 단순 필기용이 아니라, MySQL Workbench에서 직접 실행 가능한 SQL 예제와 복습 문제를 함께 정리하는 것을 목표로 합니다.

---

## 학습 흐름

| 순서 | 주제 | 문서 | 상태 |
|---|---|---|---|
| 00 | 전체 개요 | docs/00_overview.md | 완료 |
| 01 | 데이터베이스 개요 | docs/01_database_intro.md | 완료 |
| 02 | 데이터 CRUD | docs/02_crud.md | 완료 |
| 03 | 데이터 필터링 | docs/03_filtering.md | 완료 |
| 04 | 데이터 집계 | docs/04_aggregation.md | 완료 |
| 05 | 자료형 | docs/05_data_types.md | 완료 |
| 06 | 관계 만들기 | docs/06_relationship.md | 완료 |
| 07 | JOIN | docs/07_join.md | 완료 |
| 08 | 그룹화 분석 | docs/08_grouping_analysis.md | 완료 |
| 09 | 서브쿼리 | docs/09_subquery.md | 완료 |
| 10 | 데이터 모델링 | docs/10_modeling.md | 작성 예정 |

---

## 폴더 구조

~~~text
mysql-practice/
├── README.md
└── docs/
    ├── 00_overview.md
    ├── 01_database_intro.md
    ├── 02_crud.md
    ├── 03_filtering.md
    ├── 04_aggregation.md
    ├── 05_data_types.md
    ├── 06_relationship.md
    ├── 07_join.md
    ├── 08_grouping_analysis.md
    ├── 09_subquery.md
    └── 10_modeling.md
~~~

---

## 사용 환경

- DBMS: MySQL
- Tool: MySQL Workbench
- 학습 방식: 강의 내용 정리 + SQL 직접 실행 + Self Check 복습

---

## 문서 작성 규칙

각 챕터 문서는 다음 구조를 기준으로 정리합니다.

1. 학습 목표
2. 핵심 개념
3. 주요 문법
4. 실습 예제
5. 전체 실습 스크립트
6. Self Check
7. 정리

---

## 실습 방법

1. `docs/`에서 학습할 챕터 문서를 읽습니다.
2. 문서 안의 SQL 예제를 MySQL Workbench에 복사합니다.
3. 쿼리를 블록 단위로 실행합니다.
4. Self Check 문제를 먼저 직접 풀어봅니다.
5. 풀이 스크립트와 비교하면서 복습합니다.

---

## 학습 목표

이 저장소를 통해 다음 내용을 익힙니다.

- 데이터베이스와 테이블의 기본 구조 이해
- `CREATE`, `INSERT`, `SELECT`, `UPDATE`, `DELETE` 문법 학습
- `WHERE` 조건절을 활용한 데이터 필터링
- `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`를 활용한 데이터 집계
- `GROUP BY`, `HAVING`, `JOIN`, 서브쿼리 등 SQL 활용 문법 학습
