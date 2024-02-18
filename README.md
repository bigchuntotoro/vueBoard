1. node.js 설치

2. yarn 설치

npm install --global yarn

3. vue 설치
 
npm install vue

npm install -g @vue/cli

4.lombok 설치

5.MariaDB 설치

6.table 생성

CREATE TABLE BOARD(
	BNO INT NOT NULL AUTO_INCREMENT,	-- 게시판 고유 번호 (자동증가)
	TITLE VARCHAR(100),	-- 게시글 제목
	CONTENT VARCHAR(1000),	-- 게시글 내용
	WRITER VARCHAR(100),	-- 글쓴이
	REGDATE TIMESTAMP DEFAULT NOW(),	-- 날짜(기본값 현재시각)
	PRIMARY KEY (BNO)	-- 게시판 번호 기본키 지정
)

CREATE TABLE MEMBER(
	ID VARCHAR(12) NOT NULL,	-- 아이디
	PASSWORD VARCHAR(12) NOT NULL,	-- 비밀번호
	NAME VARCHAR(10) NOT NULL,	-- 이름
	DATE_OF_BIRTH DATE NOT NULL,	-- 생일
	PHONE_NUMBER VARCHAR(13) NOT NULL, -- 폰번호
	EMAIL VARCHAR(13) NOT NULL,	-- 이메일
	PRIMARY KEY(ID),	-- ID 기본키 지정
	UNIQUE KEY(EMAIL),	-- EMAIL 고유키 지정
	UNIQUE KEY(PHONE_NUMBER)	-- 폰번호 고유키 지정
);
