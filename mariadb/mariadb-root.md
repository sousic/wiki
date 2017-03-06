#mariadb root

#마지막 수정일
2017-03-07

#MariDB를 정지후, 비밀번호를 물어보지 않는 옵션으로 실행
    1. sudo systemctl stop mariadb
    2. sudo mysqld_safe --skip-grant-tables &

#root 계정으로 접속
    1. mysql -u root

#재 설정할 비밀번호를  password 에 입력
    1. use mysql;
    2. update user SET PASSWORD=PASSWORD("password") WHERE USER='root';
    3. flush privileges;
    4 . exit

#MariaDB 재시작
1. sudo systemctl start mariadb