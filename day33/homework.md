```mysql
MariaDB [testdb]> SELECT no, name regdate FROM pokemon WHERE regdate < '2020-01-01';
+----+---------+
| no | regdate |
+----+---------+
|  9 | 뮤      |
| 10 | 피츄    |
+----+---------+
2 rows in set (0.006 sec)

MariaDB [testdb]> SELECT * FROM pokemon WHERE level <= 10 AND level >= 5;
+----+----------+-------+------+------+---------------------+
| no | name     | level | hp   | ap   | regdate             |
+----+----------+-------+------+------+---------------------+
|  1 | 피카츄   |    10 |  100 |    5 | 2020-12-09 15:41:09 |
|  2 | 푸린     |     5 |  300 |   50 | 2020-12-09 15:41:09 |
|  4 | 망나뇽   |     7 |  100 |    6 | 2020-12-09 15:41:09 |
|  5 | 치코리타 |     8 |  100 |    9 | 2020-12-09 15:41:09 |
+----+----------+-------+------+------+---------------------+
4 rows in set (0.001 sec)

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
10 rows in set (0.000 sec)

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
9 rows in set (0.006 sec)

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
10 rows in set (0.000 sec)

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
10 rows in set (0.000 sec)

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
10 rows in set (0.000 sec)

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
MariaDB [testdb]>  UPDATE pokemon SET level = level + 1 WHERE level < 100;
Query OK, 9 rows affected (0.000 sec)
Rows matched: 9  Changed: 9  Warnings: 0

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
10 rows in set (0.000 sec)

MariaDB [testdb]> DELETE FROM pokemon WHERE level = 100;
Query OK, 1 row affected (0.006 sec)

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
9 rows in set (0.000 sec)
MariaDB [testdb]> UPDATE pokemon SET level = level * 2 WHERE level % 2 = 0;
Query OK, 4 rows affected (0.000 sec)
Rows matched: 4  Changed: 4  Warnings: 0

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
9 rows in set (0.000 sec)

MariaDB [testdb]> UPDATE pokemon SET level = hp / 100 WHERE hp > level*100;
Query OK, 0 rows affected (0.000 sec)
Rows matched: 0  Changed: 0  Warnings: 0

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
9 rows in set (0.000 sec)

=================================================================================================================================
MariaDB [(none)]> CREATE TABLE member()
    -> CREATE TABLE member()
    -> CREATE TABLE member()
    -> ;
ERROR 1046 (3D000): No database selected
MariaDB [(none)]> CREATE TABLE member(
    -> no INT PRIMARY KEY,
    -> id VARCHAR(40) NOT NULL UNIQUE,
    -> email VARCHAR(40) UNIQUE,
    -> password INT,
    -> type INT DEFAULT type = 1 CHECK(type >=1 AND type <=4),
    -> point INT DEFAULT point = 1000 CHECK(point > 0)
    -> );
ERROR 1046 (3D000): No database selected
MariaDB [(none)]> USE testdb
Database changed
MariaDB [testdb]> CREATE TABLE member(
    -> no INT PRIMARY KEY,
    -> id VARCHAR(40) NOT NULL UNIQUE,
    -> email VARCHAR(40) UNIQUE,
    -> password INT,
    -> type INT DEFAULT type = 1 CHECK(type >=1 AND type <=4),
    -> point INT DEFAULT point = 1000 CHECK(point > 0)
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '= 1 CHECK(type >=1 AND type <=4),
point INT DEFAULT point = 1000 CHECK(point ...' at line 6
MariaDB [testdb]> CREATE TABLE member(
    -> no INT PRIMARY KEY,
    -> id VARCHAR(40) NOT NULL UNIQUE,
    -> email VARCHAR(40) UNIQUE,
    -> password INT,
    -> type INT DEFAULT type = 1 CHECK(type >=1 AND type <=4),
    -> point INT DEFAULT point = 1000 CHECK(point > 0)
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '= 1 CHECK(type >=1 AND type <=4),
point INT DEFAULT point = 1000 CHECK(point ...' at line 6
MariaDB [testdb]> CREATE TABLE member(
    -> no INT PRIMARY KEY,
    -> id VARCHAR(40) NOT NULL UNIQUE,
    -> email VARCHAR(40) UNIQUE,
    -> password INT,
    -> type INT DEFAULT type = 1 CHECK(type >=1 AND type <=4),
    -> point INT DEFAULT point = 1000 CHECK(point > 0)
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '= 1 CHECK(type >=1 AND type <=4),
point INT DEFAULT point = 1000 CHECK(point ...' at line 6
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

MariaDB [testdb]> INSERT * FROM member;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '* FROM member' at line 1
MariaDB [testdb]> SELECT *FROM member;
+-------+-----+---------------+----------+------+-------+
| no    | id  | email         | password | type | point |
+-------+-----+---------------+----------+------+-------+
| 12131 | jkl | jkl@naver.com |    12131 |    3 |  4000 |
| 12345 | abc | abc@naver.com |    12345 |    1 |  1000 |
| 45678 | def | def@naver.com |    45678 |    1 |  2000 |
| 91011 | ghi | ghi@naver.com |    91011 |    2 |  3000 |
+-------+-----+---------------+----------+------+-------+
4 rows in set (0.000 sec)

MariaDB [testdb]> INSERT INTO QNA VALUES(1, 12345, '안녕하세요');
ERROR 1136 (21S01): Column count doesn't match value count at row 1
MariaDB [testdb]> INSERT INTO QNA(no, writer_no, content) VALUES(1, 12345, '안녕하세요');
Query OK, 1 row affected (0.024 sec)

MariaDB [testdb]> INSERT INTO QNA(no, writer_no, content) VALUES(2, 45678, '안녕하세요요요요 요');
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
