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
**bbs 테이블**
```sql
CREATE TABLE bbs(
bbs_seq INT PRIMARY KEY,
bbs_title varchar(20) NOT NULL,
bbs_writer varchar(20) NOT NULL,
bbs_content varchar(2048),
bbs_cnt int NOT NULL default 0,  
bbs_regdate datetime NOT NULL default NOW(),   
FOREIGN KEY (bbs_writer) REFERENCES user (user_ID) on delete cascade
);
```
