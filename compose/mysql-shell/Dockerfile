FROM oraclelinux:7 

ARG KEY=https://repo.mysql.com/RPM-GPG-KEY-mysql
ARG REPO=https://repo.mysql.com

ARG MYSQL_SHELL_PACKAGE_URL=$REPO/yum/mysql-tools-community/el/7/x86_64/mysql-shell-8.0.13-1.el7.x86_64.rpm

RUN rpmkeys --import $KEY \
  && yum install -y \
    $MYSQL_SHELL_PACKAGE_URL \
  && yum clean all

COPY compose/mysql-shell/run.sh /run.sh
RUN chmod +x /*.sh