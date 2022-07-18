# MySQL

## SELECT 구문 기본형식
```sql
SELECT * | 컬럼명 | 수식
[FROM] 테이블명
;
```

- DUAL 테이블
    * 테이블이 없는 경우 SELECT 구문에 대한 DUMMY 테이블명

## SELECT 구문 전체형식
```sql
5. SELECT * | 컬럼명 | 수식

1. FROM 테이블명

2. WHERE 검색조건

3. GROUP BY 그룹핑컬럼명1, 그룹핑컬럼명X

4. HAVING 그룹핑조건

6. ORDER BY 정렬컬럼명 정렬방법, 정렬컬럼명 정렬방법
;
```

## SELECT
- `*` : 테이블 구조에 맞는 모든 컬럼 순서대로


- 컬럼명A, 컬럼명C : 원하는 컬럼을 원하는 순서대로


- 수식


- 컬럼명 별명, 컬럼명 "별 명"
    * 별명에 공백이 있는 경우에는 " " 감싸주어야 함.


- DISTINCT 컬럼명1, 컬럼명X


- SUB-QUERY


## SELECT 구문 파싱(처리) 순서
- FROM WHERE GROUP HAVING SELECT ORDER