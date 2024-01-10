# TIL (_Today I Learn_)

<br/>

## 2023. 01. 01 ~ 2023. 01. 09

```

생략

```

<br/>

## 2023. 01. 10

```
[ 데이터베이스 코딩테스트 대비 ]

# 기본
SELECT 필드명 FROM 테이블명 (*는 모든 필드)

# 조건
SELECT 필드명 FROM 테이블명 WHERE 조건

# 평균
SELECT AVG(필드명) FROM 테이블명 WHERE 조건

# 평균(필드명 변경)
SELECT AVG(필드명) AS 바뀔필드명 FROM 테이블명 WHERE 조건

# 반올림
SELECT ROUND(AVG(필드명), 0) AS 바뀔필드명 FROM 테이블명 WHERE 조건

# 포맷
SELECT DATE_FORMAT(필드명, 포맷) AS 바뀔필드명
FROM 테이블명
WHERE 조건
ORDER BY 정렬조건

# NULL처리
SELECT IFNULL(필드명, NULL대신 나타낼 값) AS 바뀔필드명
FROM 테이블명
WHERE 조건
ORDER BY 정렬조건 DESC(내림차순), 정렬조건 ASC(오름차순)

# NULL처리2
SELECT 필드명
FROM 테이블명
WHERE 조건 IS NOT NULL (NULL인 값은 제외)
ORDER BY 정렬조건


* ROUND(값, 자릿수)
- 자릿수 0 : 1자리 표현
- 자릿수 N : 소숫점 아래 N자리 표현
- 자릿수 -N : 반올림하여 10의 N승자리 표현

* TRUNCATE(값, 버릴 자릿수)
- 숫자를 버릴 자릿수 아래로 버림
```

```SQL
-- 프로그래머스 평균 일일 대여 요금 구하기
-- 코드를 입력하세요
SELECT ROUND(AVG(DAILY_FEE), 0) AS AVERAGE_FEE
FROM CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE = 'SUV';
```
```SQL
-- 프로그래머스 조건에 맞는 도서 리스트 출력하기
-- 코드를 입력하세요
SELECT BOOK_ID, DATE_FORMAT(PUBLISHED_DATE, '%Y-%m-%d') AS PUBLISHED_DATE
FROM BOOK
WHERE CATEGORY = '인문' AND YEAR(PUBLISHED_DATE) = 2021
ORDER BY PUBLISHED_DATE;
```
```SQL
-- 프로그래머스 12세 이하인 여자 환자 목록 출력하기
-- 코드를 입력하세요
SELECT PT_NAME, PT_NO, GEND_CD, AGE, IFNULL(TLNO, 'NONE') AS TLNO
FROM PATIENT
WHERE AGE <= 12 AND GEND_CD = 'W'
ORDER BY AGE DESC, PT_NAME
```
```SQL
-- 프로그래머스 3월에 태어난 여성 회원 목록 출력하기
-- 코드를 입력하세요
SELECT MEMBER_ID, MEMBER_NAME, GENDER, DATE_FORMAT(DATE_OF_BIRTH, '%Y-%m-%d') AS DATE_OF_BIRTH
FROM MEMBER_PROFILE
WHERE MONTH(DATE_OF_BIRTH) = 3 AND TLNO IS NOT NULL AND GENDER = 'W'
ORDER BY MEMBER_ID
```