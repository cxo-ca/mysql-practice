# MySQL 강의 실습 정리

MySQL Workbench를 사용해서 강의 실습한 내용을 정리한 레포지토리입니다.

## Chapter 02: 데이터 CRUD

파일: `chapter02_crud.sql`

포함 내용:

- 데이터베이스 생성/삭제
  - `SHOW DATABASES;`
  - `CREATE DATABASE mapdonalds;`
  - `USE mapdonalds;`
  - `DROP DATABASE mapdonalds;`

- 테이블 생성
  - `CREATE TABLE burgers (...)`

- 데이터 삽입 (INSERT)
  - 단일 데이터 삽입
  - 다중 데이터 삽입

- 데이터 조회 (SELECT)
  - 전체 컬럼 조회
  - 특정 컬럼(name, price) 조회

- 데이터 수정 (UPDATE)
  - 전체 price 변경
  - 특정 id(기본키)를 이용한 가격 변경

- 데이터 삭제 (DELETE)
  - 특정 id의 레코드 삭제

- 테이블 삭제 (DROP TABLE)
  - `DROP TABLE burgers;`
