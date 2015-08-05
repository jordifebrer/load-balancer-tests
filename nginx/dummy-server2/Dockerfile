FROM centos:centos7
MAINTAINER Jordi Febrer <jordi.febrer@gmail.com>

RUN python -v

ADD app /tmp/app/

CMD cd /tmp/  && python -m SimpleHTTPServer 
