FROM registry.centos.org/centos/centos
RUN yum update -y
RUN yum install epel-release yum-utils -y
RUN yum install vim git wget gzip net-tools -y


RUN yum install -y npm nodejs
RUN mkdir -p /var/www/node

ARG dir=

# COPY nodejs /var/www/node/nodejs

# ENTRYPOINT node /var/www/node/node.js
