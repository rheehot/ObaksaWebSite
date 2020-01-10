**user 테이블**
```sql
CREATE TABLE user(
user_ID varchar(20) PRIMARY KEY,
user_password varchar(20) NOT NULL,
user_name varchar(20) NOT NULL,
user_age int NOT NULL,
user_gender char(1) NOT NULL check(user_gender IN('M','F')),   
user_phone char(11) UNIQUE,
user_email varchar(50) NOT NULL UNIQUE,
user_regdate datetime NOT NULL default NOW()
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
