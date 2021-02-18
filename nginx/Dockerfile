FROM amazeeio/centos:7

RUN yum install -y epel-release \
    yum check-update \
    yum update -y
RUN yum install -y nginx \
    yum clean all

EXPOSE 8080
COPY conf/drupal.conf /etc/nginx/conf.d/default.conf

RUN fix-permissions /etc/nginx

CMD ["nginx", "-g", "daemon off;"]
