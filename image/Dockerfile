FROM alizarion/centos7base:latest

MAINTAINER Michael Ward "@devoperandi"

RUN yum update -y
RUN yum install -y mod_ssl
RUN cd /tmp
RUN  wget https://github.com/pingidentity/mod_auth_openidc/releases/download/v1.8.6/mod_auth_openidc-1.8.6-1.el7.centos.x86_64.rpm

RUN yum -y install httpd mod_auth_openidc-1.8.6-1.el7.centos.x86_64.rpm

RUN rm -f /tmp/mod_auth_openidc-1.8.6-1.el7.centos.x86_64.rpm

RUN yum clean all

ADD httpd-foreground /usr/local/bin/

RUN chmod +x /usr/local/bin/httpd-foreground
RUN rm -rf /etc/httpd/logs
RUN mkdir /etc/httpd/logs
RUN rm -Rf /etc/httpd/conf.d/ssl.conf

ADD auth_openidc.conf /etc/httpd/conf.d/auth_openidc.conf

EXPOSE 443 80

CMD ["httpd-foreground"]
