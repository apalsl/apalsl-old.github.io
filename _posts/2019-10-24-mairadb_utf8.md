---
layout: post
title: "[MariaDB] 한글 깨짐"
---

create() Test를 실행하는데 SQL Error: 1366, SQLState: 22007가 발생한다.

검색해보니 Maria or Mysql에서 한글을 인식하지 못하는 문제



해결 방법은 좀 이상하다. 테이블을 생성할때 SQL 명령어를 보면 DEFAULT CHARSET=latin1이라고 나와있다. 이걸 utf8로 변경하란다.

위 방법으로 테이블 하나가 수정가능하고 밑 방법으로 데이터가 있을때 수정 가능하다.

리눅스 내부설정에서는
1)
$ sudo vi /etc/my.cnf

[mysqld]
...

default-character-set=utf8

default-collation=utf8_general_ci

...

2) database, table character set 설정

mysql> ALTER TABLE table_name convert to charset utf8;


