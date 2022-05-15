## 작성자 기준
	- ANSI 표준 함수
	- 특정 DBMS 벤더 전용 함수: MYSQL 전용, ORACLE 전용
	- 사용자 정의 함수
		* PL/SQL
		* Stored Function, Stored Procedure


## 수행결과 반환 기준
	- 단일행 함수
		* 하나의 레코드에 대해서 하나의 결과를 반환하는 함수
		* length(), trim()
	
	- 그룹(복수행 함수)
		* 여러개의 레코드에 대해서 연산 후 하나의 결과를 반환하는 함수
		* count(*), max()

## 문자관련 함수
	- length()
		* 문자길이 반환
		* 영문, 숫자 한자리는 1byte
		* 한글 한 자리는 2byte, 3byte 반환 : db 설정
		* 테이블 설계시에 한글 데이터 컬럼의 경우는 길이 * db설정byte길이
	
	- trim(), ltrim(), rtrim() : 공백 제거
		* 문자열 타입
		* char(고정길이)
		* varchar(가변길이)
			- data1 char(10)	=> 'abc       '
			- data2 varchar(10)	=> 'abc'	
	- insert(str, pos, len, newstr)
	- replace(str, from_str, to_str)
	- instr(str, substr)	
	- substring(str, pos), (str from pos), (str, pos, len), (str, from pos for len)
	- mid(str, pos, len)	
	- lower(str)
	- upper(str)	
	- concat(str1, str2, ...)

## 숫자관련 함수
	- abs(숫자) : 절댓값
	- truncate(숫자, [자릿수]) : 버림
	- round(숫자, [자릿수]) : 반올림
	- floor(숫자) : 내림
	- mod(N, M) : 나머지


## 날짜/시간 관련 함수
	- now(), sysdate(), current_timestamp()
	- current_date(), curdate()
	- current_time(), curtime()


## 복수행(그룹함수)
	- count(*), count(pk) : 전체 레코드 행수 반환
		* count(*) : null 포함 행수 반환
	- count(컬럼명) : null을 제외한 행수 반환
	- sum() : 총액
	- max() : 최대
	- min() : 최소
	- avg() : 평균