**user 테이블**
```sql
CREATE TABLE user(
	user_id VARCHAR(20) NOT NULL PRIMARY KEY,
	user_password VARCHAR(16) NOT NULL,
	user_name VARCHAR(20) NOT NULL,
	user_birth CHAR(9) NOT NULL,
	user_age INT NOT NULL,
	user_gender CHAR(1) NOT NULL,
	user_phone CHAR(11) NOT NULL UNIQUE,
	user_email VARCHAR(50) NOT NULL UNIQUE,
	user_regdate DATETIME NOT NULL DEFAULT NOW(),
	user_available INT NOT NULL DEFAULT 1
);	
```

**file 테이블**
```sql
CREATE TABLE file(
	file_seq INT AUTO_INCREMENT PRIMARY KEY,
	file_board INT NOT NULL,
	file_path VARCHAR(100) NOT NULL,
	file_content LONGBLOB NOT NULL,
	file_available INT NOT NULL DEFAULT 1,
	FOREIGN KEY (file_board) REFERENCES board(board_seq) ON UPDATE CASCADE ON DELETE CASCADE
);
```


**board 테이블**
```sql
CREATE TABLE board(
	board_seq INT AUTO_INCREMENT PRIMARY KEY,
	board_title VARCHAR(20) NOT NULL,
	board_writer varchar(20) NOT NULL,
	board_content VARCHAR(1024),
	board_regdate DATETIME NOT NULL DEFAULT NOW(),
	board_cnt INT NOT NULL DEFAULT 0,
	board_available INT NOT NULL DEFAULT 1,
	FOREIGN KEY (board_writer) REFERENCES user(user_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**comment 테이블**
```sql
CREATE TABLE comment(
	comment_seq INT AUTO_INCREMENT PRIMARY KEY,
	comment_board INT NOT NULL,
	comment_writer VARCHAR(20) NOT NULL,
	comment_content VARCHAR(512) NOT NULL,
	comment_regdate DATETIME NOT NULL DEFAULT NOW(),
	comment_available INT NOT NULL DEFAULT 1,
	FOREIGN KEY (comment_board) REFERENCES board(board_seq) ON UPDATE CASCADE ON DELETE CASCADE,
	FOREIGN KEY (comment_writer) REFERENCES user(user_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**product 테이블**
```
create table product(
	product_id INT AUTO_INCREMENT PRIMARY KEY,
	product_name VARCHAR(50) NOT NULL,
	product_price INT NOT NULL DEFAULT 0,
	product_desc VARCHAR(500),
	product_url VARCHAR(500) NOT NULL
);
```
