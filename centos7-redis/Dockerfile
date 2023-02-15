FROM registry.centos.org/centos/centos
RUN yum update -y
RUN yum install vim git wget gzip net-tools -y
RUN yum install epel-release -y
RUN yum install -y redis

COPY redis.conf /etc/redis.conf
#ENTRYPOINT /usr/bin/redis-server /etc/redis.conf --loglevel verbose