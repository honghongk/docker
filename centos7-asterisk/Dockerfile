FROM registry.centos.org/centos/centos
RUN yum update -y
RUN yum install epel-release yum-utils -y
RUN yum install vim git wget gzip net-tools -y

# 컴파일 기본
RUN yum groupinstall 'Development Tools' -y 

# 컴파일에 필요
# On many distributions, these dependencies are installed by packages with names like 'glibc-devel', 'ncurses-devel', 'openssl-devel' and 'zlib-devel' or similar.
RUN yum install libedit-devel libuuid-devel libxml2-devel sqlite-devel ncurses-devel bison kernel-headers kernel-devel newt-devel openssl-devel flex httpd-devel pjproject-devel -y

# asterisk 설치
# https://github.com/asterisk/asterisk
RUN git clone https://github.com/asterisk/asterisk.git /usr/local/src/asterisk

# 버전 선택설치
# RUN wget http://downloads.asterisk.org/pub/telephony/asterisk/

# 경로 가야함
WORKDIR /usr/local/src/asterisk 

# pjsip 의존성 설치
RUN ./contrib/scripts/install_prereq install

# RUN ./configure --with-jansson-bundled
RUN ./configure --with-ari
RUN make
RUN make install



RUN make basic-pbx

# config 샘플
RUN make samples
RUN make config
RUN ldconfig

COPY asterisk /etc/sysconfig/asterisk
COPY config /etc/asterisk

# 어차피 도커는 루트로 도니까 상관없음
# RUN adduser --system --user-group --home-dir /var/lib/asterisk --no-create-home asterisk

# v 는 로그레벨 f는 foreground
ENTRYPOINT asterisk -vvvf