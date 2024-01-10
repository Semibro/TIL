# TIL (_Today I Learn_)

<br/>

## 2024. 01. 01 ~ 2024. 01. 09

```

생략

```

<br/>

## 2024. 01. 10

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

# JOIN
SELECT A.필드명, B.필드명
FROM 테이블1 AS A
JOIN 테이블2 AS B
ON 조인조건 (A.ID = B.ID)
WHERE 조건
ORDER BY 정렬조건

# 그룹 및 그룹조건
SELECT A.필드명, B.필드명
FROM 테이블1 AS A
JOIN 테이블2 AS B
ON 조인조건
GROUP BY 그룹필드명
HAVING 그룹조건 (필드명 LIKE '서울%')
ORDER BY 정렬조건

# UNION
(SELECT 필드명
FROM 테이블 AS A
WHERE 조건
UNION
SELECT 필드명, NULL AS 필드명(필드가 없으면 NULL 처리)
FROM 테이블2 AS B
WHERE 조건)
ORDER BY 정렬조건

# LIMIT
SELECT 필드명
FROM 테이블명
ORDER BY 정렬조건
LIMIT 출력한 행의 수 (LIMIT 100, 10 -> 100번째부터 10개)


* ROUND(값, 자릿수)
- 자릿수 0 : 1자리 표현
- 자릿수 N : 소숫점 아래 N자리 표현
- 자릿수 -N : 반올림하여 10의 N승자리 표현

* TRUNCATE(값, 버릴 자릿수)
- 숫자를 버릴 자릿수 아래로 버림

* SUBSTR(값, 시작값, 끝값)
- 값의 시작값부터 끝값까지 표시
- EX) SUBSTR('2023-12-31', 1, 7) -> '2023-12'
```

```SQL
-- [프로그래머스] 평균 일일 대여 요금 구하기
-- 코드를 입력하세요
SELECT ROUND(AVG(DAILY_FEE), 0) AS AVERAGE_FEE
FROM CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE = 'SUV';
```
```SQL
-- [프로그래머스] 조건에 맞는 도서 리스트 출력하기
-- 코드를 입력하세요
SELECT BOOK_ID, DATE_FORMAT(PUBLISHED_DATE, '%Y-%m-%d') AS PUBLISHED_DATE
FROM BOOK
WHERE CATEGORY = '인문' AND YEAR(PUBLISHED_DATE) = 2021
ORDER BY PUBLISHED_DATE;
```
```SQL
-- [프로그래머스] 12세 이하인 여자 환자 목록 출력하기
-- 코드를 입력하세요
SELECT PT_NAME, PT_NO, GEND_CD, AGE, IFNULL(TLNO, 'NONE') AS TLNO
FROM PATIENT
WHERE AGE <= 12 AND GEND_CD = 'W'
ORDER BY AGE DESC, PT_NAME
```
```SQL
-- [프로그래머스] 3월에 태어난 여성 회원 목록 출력하기
-- 코드를 입력하세요
SELECT MEMBER_ID, MEMBER_NAME, GENDER, DATE_FORMAT(DATE_OF_BIRTH, '%Y-%m-%d') AS DATE_OF_BIRTH
FROM MEMBER_PROFILE
WHERE MONTH(DATE_OF_BIRTH) = 3 AND TLNO IS NOT NULL AND GENDER = 'W'
ORDER BY MEMBER_ID
```
```SQL
-- [프로그래머스] 조건에 부합하는 중고거래 댓글 조회하기
-- 코드를 입력하세요
SELECT A.TITLE, A.BOARD_ID, B.REPLY_ID, B.WRITER_ID, B.CONTENTS, DATE_FORMAT(B.CREATED_DATE, '%Y-%m-%d') AS CREATED_DATE
FROM USED_GOODS_BOARD AS A
INNER JOIN USED_GOODS_REPLY AS B
ON A.BOARD_ID = B.BOARD_ID
WHERE SUBSTR(A.CREATED_DATE, 1, 7) = '2022-10'
ORDER BY B.CREATED_DATE, A.TITLE
```
```SQL
-- [프로그래머스] 서울에 위치한 식당 목록 출력하기
-- 코드를 입력하세요
SELECT A.REST_ID, A.REST_NAME, A.FOOD_TYPE, A.FAVORITES, A.ADDRESS, ROUND(AVG(B.REVIEW_SCORE), 2) AS SCORE
FROM REST_INFO AS A
JOIN REST_REVIEW AS B
ON A.REST_ID = B.REST_ID
GROUP BY A.REST_ID
HAVING A.ADDRESS LIKE '서울%'
ORDER BY SCORE DESC, A.FAVORITES DESC
```
```SQL
-- [프로그래머스] 재구매가 일어난 상품과 회원 리스트 구하기
-- 코드를 입력하세요
SELECT USER_ID, PRODUCT_ID
FROM ONLINE_SALE
GROUP BY USER_ID, PRODUCT_ID
HAVING COUNT(USER_ID) >= 2
ORDER BY USER_ID, PRODUCT_ID DESC
```
```SQL
-- [프로그래머스] 오프라인/온라인 판매 데이터 통합하기
-- 코드를 입력하세요
(SELECT DATE_FORMAT(SALES_DATE, '%Y-%m-%d') AS SALES_DATE, PRODUCT_ID, USER_ID, SALES_AMOUNT
FROM ONLINE_SALE AS A
WHERE SUBSTR(SALES_DATE, 1, 7) = '2022-03'
UNION
SELECT DATE_FORMAT(SALES_DATE, '%Y-%m-%d') AS SALES_DATE, PRODUCT_ID, NULL AS USER_ID, SALES_AMOUNT
FROM OFFLINE_SALE AS B
WHERE SUBSTR(SALES_DATE, 1, 7) = '2022-03')
ORDER BY SALES_DATE, PRODUCT_ID, USER_ID
```
```SQL
-- [프로그래머스] 상위 n개 레코드
-- 코드를 입력하세요
SELECT NAME
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1
```

<br/>

## 2024. 01. 11

```
[ 데이터베이스 코딩테스트 대비 ]

# COUNT
SELECT COUNT(필드명) AS 바꿀필드명
FROM 테이블명
WHERE 조건

# MAX
SELECT 필드명
FROM 테이블명
WHERE 필드명 = (SELECT MAX(필드명)
              FROM 테이블명)

# DISTINCT
SELECT COUNT(DISTINCT(필드명))
FROM 테이블명
```

```SQL
-- [프로그래머스] 조건에 맞는 회원수 구하기
-- 코드를 입력하세요
SELECT COUNT(*) AS USERS
FROM USER_INFO
WHERE SUBSTR(JOINED, 1, 4) = '2021' AND AGE >= 20 AND AGE <= 29
```
```SQL
-- [프로그래머스] 가격이 제일 비싼 식품의 정보 출력하기
-- 코드를 입력하세요
SELECT *
FROM FOOD_PRODUCT
WHERE PRICE = (SELECT MAX(PRICE)
              FROM FOOD_PRODUCT)
```
```SQL
-- [프로그래머스] 중복 제거하기
-- 코드를 입력하세요
SELECT COUNT(DISTINCT(NAME))
FROM ANIMAL_INS
```