**user 테이블**
```sql
CREATE TABLE user(
user_ID varchar(20) PRIMARY KEY,
user_password varchar(20) NOT NULL,
user_name varchar(20) NOT NULL,
user_age int NOT NULL,
user_gender char(1) NOT NULL check(user_gender IN('M','F')),   
user_phone char(11)
user_email varchar(50) NOT NULL UNIQUE,
user_regdate datetime NOT NULL default NOW()
);
```
