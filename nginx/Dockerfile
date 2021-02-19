FROM amazeeio/centos:7

RUN yum install -y epel-release \
    yum check-update \
    yum update -y
RUN yum install -y nginx \
    yum clean all

EXPOSE 8080
COPY conf/drupal.conf /etc/nginx/conf.d/default.conf

RUN fix-permissions /etc/nginx
RUN curl -sLo /usr/local/bin/ep https://github.com/kreuzwerker/envplate/releases/download/v0.0.8/ep-linux && chmod +x /usr/local/bin/ep

CMD [ "/usr/local/bin/ep", "-v", "/etc/nginx/conf.d/default.conf", "--", "/usr/sbin/nginx", "-g", "daemon off;" ]
