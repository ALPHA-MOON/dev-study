#### 사용자 생성
```sql
-- 사용자 생성
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
-- 모든 IP에서 접속 가능하게 하려면
CREATE USER 'username'@'%' IDENTIFIED BY 'password';
```
> **주의:**
> 실제서비스에서는 `%`대신 특정 IP로 제한하는 것이 보안상 안전함
#### 권한 부여
```sql
-- 모든 DB에 모든 권한 부여
GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' WITH GRANT OPTION;

-- 특정 DB에만 권한 부여
GRANT SELECT, INSERT, UPDATE, DELETE ON mydb.* TO 'username'@'localhost';

-- 특정 테이블에만 권한 부여
GRANT SELECT, UPDATE ON mydb.users TO 'username'@'localhost';

-- 권한 변경사항 적용
FLUSH PRIVILEGES;

```
> 사용자별 특정 테이블만 권한 부여

#### 사용자 및 권한 조회
```sql
-- 사용자 목록 조회
SELECT user, host FROM mysql.user;

-- 특정 사용자의 권한 확인
SHOW GRANTS FOR 'username'@'localhost';

```

#### 비밀번호 변경
```sql
ALTER USER 'username'@'localhost' IDENTIFIED BY 'new_password';
```

#### 사용자 삭제
```sql
DROP USER 'username'@'localhost';

-- 사용자 삭제 후 권한 캐시가 남을 수 있으므로 FLUSH PRIVILEGES; 명령어 함께 실행
```

#### 접속 제한
```sql
-- 특정 IP에서만 접속 허용
CREATE USER 'secure_user'@'192.168.10.5' IDENTIFIED BY 'strong_pw!';

-- SSL 연결 강제
ALTER USER 'secure_user'@'%' REQUIRE SSL;

-- 비밀번호 만료 정책 설정
ALTER USER 'username'@'localhost' PASSWORD EXPIRE INTERVAL 90 DAY;
```