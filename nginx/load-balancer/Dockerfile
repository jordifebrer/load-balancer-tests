FROM centos:centos7
MAINTAINER Jordi Febrer <jordi.febrer@gmail.com>

RUN yum update -y && \
    yum install -y epel-release && \
    yum install -y nginx

ADD default.d /etc/nginx/default.d/

ADD conf.d /etc/nginx/conf.d/

CMD nginx -g "daemon off;"

