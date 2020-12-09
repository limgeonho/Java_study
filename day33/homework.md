```mysql
등록일자가 2020/01/01 이전인 포켓몬들의 번호, 이름, 등록일자 알려줘
MariaDB [testdb]> SELECT no, name regdate FROM pokemon WHERE regdate < '2020-01-01';
+----+---------+
| no | regdate |
+----+---------+
|  9 | 뮤      |
| 10 | 피츄    |
+----+---------+

레벨이 5 이상 10 이하인 포켓몬들의 모든 정보 알려줘 
MariaDB [testdb]> SELECT * FROM pokemon WHERE level <= 10 AND level >= 5;
+----+----------+-------+------+------+---------------------+
| no | name     | level | hp   | ap   | regdate             |
+----+----------+-------+------+------+---------------------+
|  1 | 피카츄   |    10 |  100 |    5 | 2020-12-09 15:41:09 |
|  2 | 푸린     |     5 |  300 |   50 | 2020-12-09 15:41:09 |
|  4 | 망나뇽   |     7 |  100 |    6 | 2020-12-09 15:41:09 |
|  5 | 치코리타 |     8 |  100 |    9 | 2020-12-09 15:41:09 |
+----+----------+-------+------+------+---------------------+

모든 포켓몬들의 레벨 보여줘
MariaDB [testdb]> SELECT level FROM pokemon;
+-------+
| level |
+-------+
|    10 |
|     5 |
|     3 |
|     7 |
|     8 |
|    90 |
|    15 |
|   100 |
|    30 |
|    30 |
+-------+

모든 포켓몬들의 레벨 보여줘. 중복 제거 해줘. (DISTINCT)  
MariaDB [testdb]> SELECT DISTINCT level FROM pokemon;
+-------+
| level |
+-------+
|    10 |
|     5 |
|     3 |
|     7 |
|     8 |
|    90 |
|    15 |
|   100 |
|    30 |
+-------+

모든 포켓몬들의 이름, 레벨 보여줘. 이름 오름차순으로 보여줘  (ORDER BY) 
MariaDB [testdb]>  SELECT name, level FROM pokemon ORDER BY name;
+----------+-------+
| name     | level |
+----------+-------+
| 닥트리오 |   100 |
| 뚜벅초   |    15 |
| 라이츄   |     3 |
| 망나뇽   |     7 |
| 뮤       |    30 |
| 잠만보   |    90 |
| 치코리타 |     8 |
| 푸린     |     5 |
| 피츄     |    30 |
| 피카츄   |    10 |
+----------+-------+

모든 포켓몬들의 이름, 레벨 보여줘. 레벨 많은 순으로 보여줘  (ORDER BY) 
MariaDB [testdb]> SELECT name, level FROM pokemon ORDER BY level;
+----------+-------+
| name     | level |
+----------+-------+
| 라이츄   |     3 |
| 푸린     |     5 |
| 망나뇽   |     7 |
| 치코리타 |     8 |
| 피카츄   |    10 |
| 뚜벅초   |    15 |
| 뮤       |    30 |
| 피츄     |    30 |
| 잠만보   |    90 |
| 닥트리오 |   100 |
+----------+-------+

모든 포켓몬들의 이름, 레벨 보여줘. 레벨 많은 순으로 보여줘  (ORDER BY) 
MariaDB [testdb]> SELECT name, level FROM pokemon ORDER BY level DESC;
+----------+-------+
| name     | level |
+----------+-------+
| 닥트리오 |   100 |
| 잠만보   |    90 |
| 뮤       |    30 |
| 피츄     |    30 |
| 뚜벅초   |    15 |
| 피카츄   |    10 |
| 치코리타 |     8 |
| 망나뇽   |     7 |
| 푸린     |     5 |
| 라이츄   |     3 |
+----------+-------+

레벨이 3이상인 모든 포켓몬들의 이름, 레벨 보여줘. 레벨 많은 순으로, 같은 레벨이면 이름 오름차순으로 보여줘  (ORDER BY)
MariaDB [testdb]> SELECT name, level FROM pokemon WHERE level >= 3  ORDER BY level DESC, name;
+----------+-------+
| name     | level |
+----------+-------+
| 닥트리오 |   100 |
| 잠만보   |    90 |
| 뮤       |    30 |
| 피츄     |    30 |
| 뚜벅초   |    15 |
| 피카츄   |    10 |
| 치코리타 |     8 |
| 망나뇽   |     7 |
| 푸린     |     5 |
| 라이츄   |     3 |
+----------+-------+

모든 포켓몬들의 이름, 레벨 보여줘. 등록일자 최신순으로 보여줘.
MariaDB [testdb]> SELECT name, level FROM pokemon ORDER BY regdate ASC;
+----------+-------+
| name     | level |
+----------+-------+
| 피츄     |    30 |
| 뮤       |    30 |
| 뚜벅초   |    15 |
| 잠만보   |    90 |
| 치코리타 |     8 |
| 망나뇽   |     7 |
| 라이츄   |     3 |
| 푸린     |     5 |
| 피카츄   |    10 |
| 닥트리오 |   100 |
+----------+-------+

레벨이 100 미만인 포켓몬들의 레벨을 1씩 증가해줘
MariaDB [testdb]>  UPDATE pokemon SET level = level + 1 WHERE level < 100;
MariaDB [testdb]> SELECT *FROM pokemon;
+----+----------+-------+------+------+---------------------+
| no | name     | level | hp   | ap   | regdate             |
+----+----------+-------+------+------+---------------------+
|  1 | 피카츄   |    11 |  100 |    5 | 2020-12-09 15:41:09 |
|  2 | 푸린     |     6 |  300 |   50 | 2020-12-09 15:41:09 |
|  3 | 라이츄   |     4 |  100 |    5 | 2020-12-09 15:41:09 |
|  4 | 망나뇽   |     8 |  100 |    6 | 2020-12-09 15:41:09 |
|  5 | 치코리타 |     9 |  100 |    9 | 2020-12-09 15:41:09 |
|  6 | 잠만보   |    91 |  100 |   10 | 2020-12-09 15:41:09 |
|  7 | 뚜벅초   |    16 |  100 |    2 | 2020-12-09 15:41:09 |
|  8 | 닥트리오 |   100 | NULL | NULL | 2020-12-09 15:41:10 |
|  9 | 뮤       |    31 | NULL | NULL | 2019-11-28 22:10:03 |
| 10 | 피츄     |    31 | NULL | NULL | 2019-02-28 12:14:23 |
+----+----------+-------+------+------+---------------------+

포켓몬 중 레벨이 100 인 포켓몬들을 삭제해줘
MariaDB [testdb]> DELETE FROM pokemon WHERE level = 100;
MariaDB [testdb]> SELECT *FROM pokemon;
+----+----------+-------+------+------+---------------------+
| no | name     | level | hp   | ap   | regdate             |
+----+----------+-------+------+------+---------------------+
|  1 | 피카츄   |    11 |  100 |    5 | 2020-12-09 15:41:09 |
|  2 | 푸린     |     6 |  300 |   50 | 2020-12-09 15:41:09 |
|  3 | 라이츄   |     4 |  100 |    5 | 2020-12-09 15:41:09 |
|  4 | 망나뇽   |     8 |  100 |    6 | 2020-12-09 15:41:09 |
|  5 | 치코리타 |     9 |  100 |    9 | 2020-12-09 15:41:09 |
|  6 | 잠만보   |    91 |  100 |   10 | 2020-12-09 15:41:09 |
|  7 | 뚜벅초   |    16 |  100 |    2 | 2020-12-09 15:41:09 |
|  9 | 뮤       |    31 | NULL | NULL | 2019-11-28 22:10:03 |
| 10 | 피츄     |    31 | NULL | NULL | 2019-02-28 12:14:23 |
+----+----------+-------+------+------+---------------------+

레벨이 짝수인 포켓몬들의 레벨을 두배로 변경해줘
MariaDB [testdb]> UPDATE pokemon SET level = level * 2 WHERE level % 2 = 0;
MariaDB [testdb]> SELECT *FROM pokemon;
+----+----------+-------+------+------+---------------------+
| no | name     | level | hp   | ap   | regdate             |
+----+----------+-------+------+------+---------------------+
|  1 | 피카츄   |    11 |  100 |    5 | 2020-12-09 15:41:09 |
|  2 | 푸린     |    12 |  300 |   50 | 2020-12-09 15:41:09 |
|  3 | 라이츄   |     8 |  100 |    5 | 2020-12-09 15:41:09 |
|  4 | 망나뇽   |    16 |  100 |    6 | 2020-12-09 15:41:09 |
|  5 | 치코리타 |     9 |  100 |    9 | 2020-12-09 15:41:09 |
|  6 | 잠만보   |    91 |  100 |   10 | 2020-12-09 15:41:09 |
|  7 | 뚜벅초   |    32 |  100 |    2 | 2020-12-09 15:41:09 |
|  9 | 뮤       |    31 | NULL | NULL | 2019-11-28 22:10:03 |
| 10 | 피츄     |    31 | NULL | NULL | 2019-02-28 12:14:23 |
+----+----------+-------+------+------+---------------------+

체력이 레벨의 100배보다 큰 포켓몬들의 레벨을 체력의 1/100로 수정해줘
MariaDB [testdb]> UPDATE pokemon SET level = hp / 100 WHERE hp > level*100;
MariaDB [testdb]> SELECT *FROM pokemon;
+----+----------+-------+------+------+---------------------+
| no | name     | level | hp   | ap   | regdate             |
+----+----------+-------+------+------+---------------------+
|  1 | 피카츄   |    11 |  100 |    5 | 2020-12-09 15:41:09 |
|  2 | 푸린     |    12 |  300 |   50 | 2020-12-09 15:41:09 |
|  3 | 라이츄   |     8 |  100 |    5 | 2020-12-09 15:41:09 |
|  4 | 망나뇽   |    16 |  100 |    6 | 2020-12-09 15:41:09 |
|  5 | 치코리타 |     9 |  100 |    9 | 2020-12-09 15:41:09 |
|  6 | 잠만보   |    91 |  100 |   10 | 2020-12-09 15:41:09 |
|  7 | 뚜벅초   |    32 |  100 |    2 | 2020-12-09 15:41:09 |
|  9 | 뮤       |    31 | NULL | NULL | 2019-11-28 22:10:03 |
| 10 | 피츄     |    31 | NULL | NULL | 2019-02-28 12:14:23 |
+----+----------+-------+------+------+---------------------+


=================================================================================================================================

1. MEMBER 테이블 만들기 
	    항목 : 회원번호(no), 아이디(id), 패스워드(password), 이메일(email), 등급(type), 적립금(point)
 	    제약조건 : 
		Primary key 는 회원번호다.
		아이디는 중복이면 안된다. (UNIQUE) 
		이메일도 중복이면 안된다. (UNIQUE) 
		아이디는 누락되면 안된다. (NOT NULL)
		등급은 1 ~ 4가 있고 기본값은 1이다.
		적립금은 1000원이 기본값이고 음수일 수 없다.
	
MariaDB [testdb]> CREATE TABLE member(
    -> no INT PRIMARY KEY,
    -> id VARCHAR(40) NOT NULL UNIQUE,
    -> email VARCHAR(40) UNIQUE,
    -> password INT,
    -> type INT DEFAULT 1 CHECK(type >=1 AND type <=4),
    -> point INT DEFAULT 1000 CHECK(point > 0)
    -> );
Query OK, 0 rows affected (0.019 sec)

MariaDB [testdb]> DESC member;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| no       | int(11)     | NO   | PRI | NULL    |       |
| id       | varchar(40) | NO   | UNI | NULL    |       |
| email    | varchar(40) | YES  | UNI | NULL    |       |
| password | int(11)     | YES  |     | NULL    |       |
| type     | int(11)     | YES  |     | 1       |       |
| point    | int(11)     | YES  |     | 1000    |       |
+----------+-------------+------+-----+---------+-------+
6 rows in set (0.019 sec)

2. QNA 테이블 만들기 
	    항목 : 질문번호(no), 글쓴이번호(writer_no), 질문 내용(content), 등록일자(regdate)
	    제약조건 : 
		Primary key 는 질문번호다.
		글쓴이번호는 MEMBER 테이블의 회원번호를 참조한다. (FOREIGN KEY)
		글쓴이 회원이 삭제되면 해당 질문도 삭제된다. (CASCADE)	
		질문 내용은 누락되면 안된다.
		등록일자는 기본값이 현재 시간이다. 

MariaDB [testdb]> CREATE TABLE QNA(
    -> no INT PRIMARY KEY,
    -> writer_no INT,
    -> content TEXT NOT NULL,
    -> regdate DATETIME DEFAULT CURRENT_TIMESTAMP,
    -> FOREIGN KEY(writer_no) references member(no) ON DELETE CASCADE
    -> );
Query OK, 0 rows affected (0.019 sec)

MariaDB [testdb]> INSERT INTO member VALUES(12345, 'abc', 'abc@naver.com', 12345, 1, 1000);
Query OK, 1 row affected (0.017 sec)

MariaDB [testdb]> INSERT INTO member VALUES(45678, 'def', 'def@naver.com', 45678, 1, 2000);
Query OK, 1 row affected (0.017 sec)

MariaDB [testdb]> INSERT INTO member VALUES(91011, 'ghi', 'ghi@naver.com', 91011, 2, 3000);
Query OK, 1 row affected (0.017 sec)

MariaDB [testdb]> INSERT INTO member VALUES(12131, 'jkl', 'jkl@naver.com', 12131, 3, 4000);
Query OK, 1 row affected (0.016 sec)

MariaDB [testdb]> SELECT *FROM member;
+-------+-----+---------------+----------+------+-------+
| no    | id  | email         | password | type | point |
+-------+-----+---------------+----------+------+-------+
| 12131 | jkl | jkl@naver.com |    12131 |    3 |  4000 |
| 12345 | abc | abc@naver.com |    12345 |    1 |  1000 |
| 45678 | def | def@naver.com |    45678 |    1 |  2000 |
| 91011 | ghi | ghi@naver.com |    91011 |    2 |  3000 |
+-------+-----+---------------+----------+------+-------+

MariaDB [testdb]> INSERT INTO QNA(no, writer_no, content) VALUES(1, 12345, '안녕하세요');
Query OK, 1 row affected (0.024 sec)

MariaDB [testdb]> INSERT INTO QNA(no, writer_no, content) VALUES(2, 45678, '안녕하세요요요요요');
Query OK, 1 row affected (0.017 sec)

MariaDB [testdb]> SELECT * FROM QNA;
+----+-----------+--------------------+---------------------+
| no | writer_no | content            | regdate             |
+----+-----------+--------------------+---------------------+
|  1 |     12345 | 안녕하세요         | 2020-12-09 22:15:32 |
|  2 |     45678 | 안녕하세요요요요요 | 2020-12-09 22:15:57 |
+----+-----------+--------------------+---------------------+
2 rows in set (0.000 sec)

MariaDB [testdb]> DELETE FROM member WHERE no = 12345;
Query OK, 1 row affected (0.031 sec)

MariaDB [testdb]> SELECT * FROM QNA;
+----+-----------+--------------------+---------------------+
| no | writer_no | content            | regdate             |
+----+-----------+--------------------+---------------------+
|  2 |     45678 | 안녕하세요요요요요 | 2020-12-09 22:15:57 |
+----+-----------+--------------------+---------------------+
1 row in set (0.000 sec)

```
