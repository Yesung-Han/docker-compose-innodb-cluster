# docker-compose-innodb-cluster

mysql dev 블로그에 올라온 [포스트](https://dev.mysql.com/blog-archive/docker-compose-setup-for-innodb-cluster/)를 참고하여 작성되었습니다.

fork from
https://github.com/neumayer/mysql-docker-compose-examples/tree/master/innodb-cluster



HOW TO START

```
docker-compose up --build  // 최초 이미지 빌드 & docker-compose 실행
docker-compose up // docker-compose 실행
```

HOW TO END
```
docker-compose down // 컨테이너 중지
docker-compose down -v // 컨테이너 중지 및 볼륨 및 관련 네트워크 삭제
```

## 클러스터 구성

1. 프라이머리 서버 : mysql-server-1
  - image: mysql/mysql-server:8.0.12
  - ports: 3301:3306
2. 세컨더리 서버 1 : mysql-server-2
  - image: mysql/mysql-server:8.0.12
  - ports: 3302:3306
3. 세컨더리 서버 2 : mysql-server-3
  - image: mysql/mysql-server:8.0.12
  - ports: 3303:3306
4. mysql-shell
  - 환경: oraclelinux:7
  - mysql-shell-8.0.13-1.el7.x86_64.rpm 설치
5. mysql-router
  - image: mysql/mysql-router:8.0
  - ports: 6446:6446
6. 예시 어플리케이션 서버 : dbwebapp
  - image: neumayer/dbwebapp
  - ports: 8080:8080
  
