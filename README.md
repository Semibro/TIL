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

# IFNULL
SELECT IFNULL(필드명, NULL대신 표시할 값)
FROM 테이블명
WHERE 조건
ORDER BY 정렬조건

# IS NULL
SELECT 필드명
FROM 테이블명
WHERE 필드명 IS NULL
ORDER BY 정렬조건

# GROUP BY 활용
SELECT 필드명
FROM 테이블명
WHERE 필드명 IN SELECT 필드명
                FROM 테이블명
                GROUP BY 필드명
ORDER BY 정렬조건

# JOIN + GROUP BY
SELECT 필드명
FROM 테이블명1 AS A
JOIN 테이블명2 AS B
ON 필드명1 = 필드명2
WHERE 조건
GROUP BY 그룹필드
HAVING 그룹조건
ORDER BY 정렬조건

# CASE
SELECt 필드명
    CASE
        WHEN 조건 THEN 나타낼 값
        ELSE 다른 값
    END 필드명
FROM 테이블명
WHERE 조건
GROUP BY 필드명
ORDER BY 정렬조건

* IFNULL
- SELECT IFNULL(컬럼명, 0) FROM 테이블명 : 0으로 치환

* IF
- SELECT IF(컬럼명 IS NULL, '1', '2') FROM 테이블명 : NULL일 경우 1, 아니면 2를 출력

* NULLIF
- SELECT NULLIF(1, 1) : (전자 = 후자)의 결과가 false면 전자의 값을 출력하고, true면 NULL을 출력

* GROUP BY
- GROUP BY로 묶으면 가장 상단에 있는 데이터를 임의로 가져온다. 즉, GROUP BY로 묶은 그룹 중 첫 번째 값을 가져온다.

* SQL의 쿼리 실행 순서
- FROM절(+ JOIN) : 테이블 전체를 가져오는 역할, 테이블을 합쳐주는 JOIN도 동순위!
- WHERE절 : FROM에서 가져온 테이블을 WHERE절을 통해 원하는 조건에 맞는 값만 필터링해주는 역할
- GROUP BY : 컬럼을 그룹핑, 가장 상단의 데이터를 임의로 가져온다.
- HAVING절 : GROUP BY를 통해 그룹핑 후 그룹에 사용하는 조건절, WHERE와 HAVING이 둘 다 사용 가능하다면 WHERE를 사용하는 것이 적절
- SELECT절 : 위의 절들을 실행 후 어떤 컬럼을 출력할지 선택
- ORDER BY절 : 출력할 컬럼의 순서를 어떠한 방식으로 정렬할지 선택
- LIMIT : 최종 결과물을 몇 개까지 보여줄지 선택
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
```SQL
-- [프로그래머스] 경기도에 위치한 식품창고 목록 출력하기
-- 코드를 입력하세요
SELECT WAREHOUSE_ID, WAREHOUSE_NAME, ADDRESS, IFNULL(FREEZER_YN, 'N') AS FREEZER_YN
FROM FOOD_WAREHOUSE
WHERE ADDRESS LIKE '경기%'
ORDER BY WAREHOUSE_ID
```
```SQL
-- [프로그래머스] 이름이 없는 동물의 아이디
-- 코드를 입력하세요
SELECT ANIMAL_ID
FROM ANIMAL_INS
WHERE NAME IS NULL
ORDER BY ANIMAL_ID
```
```SQL
-- [프로그래머스] 즐겨찾기가 가장 많은 식당 정보 출력하기
-- 코드를 입력하세요
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
FROM REST_INFO
WHERE (FOOD_TYPE, FAVORITES) IN (SELECT FOOD_TYPE, MAX(FAVORITES)
                                FROM REST_INFO
                                GROUP BY FOOD_TYPE)
ORDER BY FOOD_TYPE DESC
```
```SQL
-- [프로그래머스] 조건에 맞는 사용자와 총 거래금액 조회하기
-- 코드를 입력하세요
SELECT B.USER_ID, B.NICKNAME, SUM(A.PRICE) AS TOTAL_SALES
FROM USED_GOODS_BOARD AS A
JOIN USED_GOODS_USER AS B
ON A.WRITER_ID = B.USER_ID
WHERE A.STATUS = 'DONE'
GROUP BY A.WRITER_ID
HAVING TOTAL_SALES >= 700000
ORDER BY TOTAL_SALES
```
```SQL
-- [프로그래머스] 자동차 대여 기록에서 대여중 / 대여 가능 여부 구분하기
-- 코드를 입력하세요
SELECT CAR_ID,
    CASE
        WHEN CAR_ID IN (SELECT CAR_ID
                       FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
                       WHERE '2022-10-16' BETWEEN START_DATE AND END_DATE) THEN '대여중'
        ELSE '대여 가능'
    END "AVAILABILITY"
FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
GROUP BY CAR_ID
ORDER BY CAR_ID DESC
```
```SQL
-- [프로그래머스] 자동차 종류 별 특정 옵션이 포함된 자동차 수 구하기
-- OPTIONS의 값은 하나의 문자열로 보기 때문에 포함여부를 확인!
-- 코드를 입력하세요
SELECT CAR_TYPE, COUNT(CAR_TYPE) AS CARS
FROM CAR_RENTAL_COMPANY_CAR
WHERE OPTIONS LIKE '%통풍시트%' OR OPTIONS LIKE '%열선시트%' OR OPTIONS LIKE '%가죽시트%'
GROUP BY CAR_TYPE
ORDER BY CAR_TYPE
```
```SQL
-- [프로그래머스] 대여 횟수가 많은 자동차들의 월별 대여 횟수 구하기
-- 코드를 입력하세요
SELECT MONTH(START_DATE) AS MONTH, CAR_ID, COUNT(*) AS RECORDS
FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
WHERE START_DATE BETWEEN '2022-08-01' AND '2022-10-31'
    AND CAR_ID IN (SELECT CAR_ID
                  FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
                  WHERE START_DATE BETWEEN '2022-08-01' AND '2022-10-31'
                  GROUP BY CAR_ID
                  HAVING COUNT(CAR_ID) >= 5)
GROUP BY CAR_ID, MONTH(START_DATE)
HAVING RECORDS > 0
ORDER BY MONTH, CAR_ID DESC
```

<br/>

## 2024. 01. 12

```

[ 데이터베이스 코딩테스트 대비 ]

# DATEDIFF
- SELECT DATEDIFF('구분자', 'Start_Date', 'End_Date')

# AVG
- AVG(DATEDIFF(END_DATE, START_DATE)+1)
```
```SQL
-- [프로그래머스] 자동차 대여 기록에서 장기/단기 대여 구분하기
-- 코드를 입력하세요
SELECT HISTORY_ID, CAR_ID, DATE_FORMAT(START_DATE, '%Y-%m-%d') AS START_DATE, DATE_FORMAT(END_DATE, '%Y-%m-%d') AS END_DATE,
    CASE
        WHEN DATEDIFF(END_DATE, START_DATE) < 29 THEN '단기 대여'
        ELSE '장기 대여'
    END AS RENT_TYPE
FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
WHERE START_DATE LIKE '2022-09%'
ORDER BY HISTORY_ID DESC
```
```SQL
-- [프로그래머스] 자동차 평균 대여 기간 구하기
-- 코드를 입력하세요
SELECT CAR_ID, ROUND(AVG(DATEDIFF(END_DATE, START_DATE)+1), 1) AS AVERAGE_DURATION
FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
GROUP BY CAR_ID
HAVING AVG(DATEDIFF(END_DATE, START_DATE)+1) >= 7
ORDER BY AVERAGE_DURATION DESC, CAR_ID DESC
```

#### DATEDIFF 구분자
||구분자|약어|
|---|---|---|
|년도|year|yy, yyyy|
|분기|quarter|qq, q|
|월|month|mm, m|
|일|day|dd, d|
|주|week|wk|
|시간|hour|m|
|분|minute|mi, n|
|초|second|ss, s|
|밀리초|millisecond|ms|
|마이크로초|microsecond|mcs|
|나노초|nanosecond|ns|

#### SQL 함수 정리
|함수|사용 예시|출력결과|
|---|---|---|
|절대값 ABS|```SELECT ABS(-10) AS 절대값 FROM TABLE```|10|
|소수점 n자리 버리기 FLOOR|```SELECT FLOOR(34.56789) FROM TABLE```|34|
|반올림 ROUND|```SELECT ROUND(34.56789)```|35|
|지정 자리수 자르기 TRUNC|```SELECT TRUNC(34.5678, 2), TRUNC(34.5678, -1), TRUNC(34.5678) FROM TABLE```|34.56  30  34|
|나머지 리턴 MOD|```SELECT MOD(27, 2) FROM TABLE```|1|
|대문자 변환 UPPER|```SELECT UPPER('Welcome to MySQL') FROM TABLE```|WELCOME TO MYSQL|
|소문자 변환 LOWER|```SELECT LOWER('Welcome to MySQL') FROM TABLE```|welcome to mysql|
|이니셜만 대문자 변환 INITCAP|```SELECT INITCAP('weLcoMe oT mYsQl') FROM TABLE```|Welcome To Mysql|
|문자열 길이 LENGTH|```SELECT LENGTH('MySQL'), LENGTH('마이에스큐엘') FROM TABLE```|5  6|
|문자열 일부 추출 SUBSTR|```SELECT SUBSTR('Welcome to MySQL', 4, 4) FROM TABLE```|come|
|특정문자 위치 리턴 INSTR|```SELECT INSTR('WELCOME TO MYSQL', 'L') FROM TABLE```|3|
|왼쪽 특정 기호 채우기 LPAD|```SELECT LPAD('MySQL', 10, '$') FROM TABLE```|$$$$$MySQL|
|오른쪽 특정 기호 채우기 RPAD|```SELECT LPAD('MySQL', 10, '$') FROM TABLE```|MySQL$$$$$|
|문자열 공백 제거 TRIM|```SELECT TRIM('     MySQL     ') FROM TABLE```|MySQL|
|시스템 날짜 리턴 SYSDATE|```SELECT SYSDATE FROM TABLE```|24/01/12|
|날짜 사이 간격 일 수 리턴 MONTHS_BETWEEN|```SELECT ENAME AS '이름', SYSDATE AS '오늘', HIREDATE AS '입사일', MONTHS_BETWEEN(SYSDATE, HIREDATE) AS '근무일' FROM TABLE```|489.456265456|
|개월 수 구하기 ADD_MONTHS|```SELECT ENAME AS '이름', SYSDATE AS '오늘', HIREDATE AS '입사일', ADD_MONTHS(HIREDATE, 6) AS '입사 6개월 후' FROM TABLE```|23/07/12|
|지정 월의 마지막 날을 반환 LAST_DAY|```SELECT LAST_DAY(SYSDATE) FROM TABLE```|24/01/31|
|날짜 형식 변환 출력 TO_CHAR|```SELECT TO_CHAR(SYSDATE, 'YYYY-MM-DD') FROM TABLE```|2024-01-12|
|숫자 형식 변환 출력 TO_CHAR|```SELECT ENAME AS 이름, SAL AS 연봉, TO_CHAR(SAL, 'L999,999') FROM TABLE```|₩2,677|
|NULL값 변환 NVL|```SELECT NVL(COMM, 0) FROM TABLE```|NULL이 0으로 변환|

#### 파이썬 지역 개념
```Python
# global 범위
def outer():
    # outer() 함수 입장에서 local 범위
    # inner() 함수 입장에서 nonlocal 범위
    def inner():
        # inner() 함수 입장에서 local 범위
```
```Python
# [프로그래머스] 타겟 넘버
def solution(numbers, target):
    answer = 0
    def dfs(idx, num):
        if idx == len(numbers):
            if num == target:
                nonlocal answer
                answer += 1
            return
        else:
            dfs(idx+1, num+numbers[idx])
            dfs(idx+1, num-numbers[idx])
    dfs(0, 0)
    return answer
```

<br/>

## 2024. 01. 13

```
[ 코딩테스트 후기 ]

1번 문제는 무난한 구현 문제였다. 생각했던대로 구현했고, 테스트 케이스에서 문제가 없어서 그냥 패스

2번 문제도 구현이였는데.. 어떻게 접근해야하는지 생각이 나지 않아서 나중에 풀어야겠다 생각하고 넘어감. (결국 못풀었다..ㅠ)

3번 문제는 DFS였는데, 나중에 들어보니 DP+DFS?라는 소리를 들었다. 일단 DFS구현했고 테스트케이스에서 이상이 없어서 해결!

SQL 1번 문제는 무난한 WHERE ORDER BY를 사용하는 문제! 서류 합격 결과 나오고 SQL 공부한게 효과는 있었다.

SQL 2번 문제는 JOIN하는 문제였는데.. 분명 맞게 푼 것 같은데 0개일 때, 출력이 안됐다. 해결 방법에 대해서 좀 더 고민해 볼 필요가 있는듯하다.
```

<br/>

## 2024. 01. 14

```
NCS로 인한 생략
```

<br/>

## 2024. 01. 15

```
면접으로 인한 생략
```

<br/>

## 2024. 01. 16 ~ 2024. 01. 21

```
생략...
```

<br/>

## 2024. 01. 22

```
어려운 문제는 아니였지만, 오랜만에 그냥 깡구현 문제를 풀어서 기억에 남기고자 작성
```

[백준 20125](https://www.acmicpc.net/problem/20125)
```python
N = int(input())
x, y, Larm, Rarm, core, Lleg, Rleg = 0, 0, 0, 0, 0, 0, 0

for i in range(N):
    for j, cookie in enumerate(list(input())):
        if x == 0 and y == 0 and cookie == '*':
            x, y = i+1, j
        elif i == x and j < y and cookie == '*':
            Larm += 1
        elif i == x and j > y and cookie == '*':
            Rarm += 1
        elif i > x and j == y and cookie == '*':
            core += 1
        elif i > x+core and j < y and cookie == '*':
            Lleg += 1
        elif i > x+core and j > y and cookie == '*':
            Rleg += 1

print(x+1, y+1)
print(Larm, Rarm, core, Lleg, Rleg)
```

<br/>

## 2024. 01. 23

```
알고리즘
```

[등수 구하기](https://github.com/Semibro/Algorithm/tree/main/%EB%B0%B1%EC%A4%80/Silver/1205.%E2%80%85%EB%93%B1%EC%88%98%E2%80%85%EA%B5%AC%ED%95%98%EA%B8%B0)

[크로스 컨트리](https://github.com/Semibro/Algorithm/tree/main/%EB%B0%B1%EC%A4%80/Silver/9017.%E2%80%85%ED%81%AC%EB%A1%9C%EC%8A%A4%E2%80%85%EC%BB%A8%ED%8A%B8%EB%A6%AC)

<br/>

## 2024. 01. 24

```
알고리즘
```

[어두운 굴다리](https://github.com/Semibro/Algorithm/tree/738a9edc956e100a4d1631113e95e84c916627af)

[빗물](https://github.com/Semibro/Algorithm/tree/58aa3955f2d9fce780adaa949b44102c8dcdc6f9)

<br/>

```
React를 사용하여 start버튼을 클릭하면 숫자가 1초마다 1씩 오르고 다시 누르면 멈추는 코드 작성
```

```JavaScript
import React, { useState } from 'react';
import './App.css';

function App() {
  const [timer, setTimer] = useState(0)
  const [intervalCheck, setIntervalCheck] = useState(null)

  const startFunction = () => {
    if (intervalCheck) {
      clearInterval(intervalCheck)
      setIntervalCheck(null)
    } else {
      const id = setInterval(() => {
        setTimer((prev) => prev + 1)
      }, 1000)

      setIntervalCheck(id)
    }
  }

  return (
    <div>
      <h1>Tasks 추가</h1>
      <div>
        <div>
          number: {timer}
        </div>
        <div>
          start: <button onClick={startFunction}>start</button>
        </div>
      </div>
    </div>
  );
}

export default App;

```

<br/>

## 2024. 01. 25

```
알고리즘
```

[예산](https://github.com/Semibro/Algorithm/tree/43ead8e573395e6eb7cbf54e76d6789812a51c73/%EB%B0%B1%EC%A4%80/Silver/2512.%E2%80%85%EC%98%88%EC%82%B0)

```
[ Axios ]


- Node.js와 브라우저를 위한 Promise 기반 HTTP 비동기 통신 라이브러리

- 비동기로 HTTP 통신을 가능하게 해주고, REST API에 데이터를 요청할 때, promise 객체로 return 해주기 때문에 response 데이터를 다루기가 쉽다.

- 설치 : npm install axios

- 모듈 import : import axios from 'axios'


[ Promise ]


- JS에서 제공하는 비동기를 간편하게 처리할 수 있게 도와주는 객체

- promise는 성공 또는 실패를 할 수 있다.
```

```
[ Axios HTTP Method ]

axios.get(url) : url이 존재하는 자원에 요청 후, 데이터를 받아오는 방식
axios.delete(url) : DB에 저장된 내용을 삭제하는 목적으로 사용
axios.post(url, data) : 새로운 데이터를 생성할 때 사용
axios.put(url, data) : DB에 저장된 내용을 갱신하는데 사용
```

#### 예시
```JavaScript
axios.get('/url')
  .then((res) => {
    console.log(res.data)
  })
  .catch((err) => {
    console.log(err)
  })

axios.delete('/url', {
  params: {
    uuid: 1
  }
})
  .then((res) => {
    console.log(res.data)
  })
  .catch((err) => {
    console.log(err)
  })

axios.post('/url', {
  firstName: 'JunHyung',
  lastName: 'Kim'
})
  .then((res) => {
    console.log(res.data)
  })
  .catch((err) => {
    console.log(err)
  })

axios.put('/url', {
  uuid: 1,
  name: 'Kim',
})
  .then((res) => {
    console.log(res.data)
  })
  .catch((err) => {
    console.log(err)
  })
```