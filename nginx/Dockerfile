#This is my first Dockerfile
#Version 1.0
#Author: 260591808@qq.com

#Base images
FROM alpine

#MAINTAINER
MAINTAINER 260591808@qq.com

#ADD
ADD ./pkg/nginx-1.14.0.tar.gz /usr/local/src

#WORKDIR
WORKDIR /usr/local/src/nginx-1.14.0

#RUN
RUN apk add --no-cache gcc g++ make zlib-dev pcre-dev openssl-dev --repository http://mirrors.aliyun.com/alpine/v3.8/main/ \
    && addgroup www \
    && adduser -s /sbin/nologin -D -G www -H www \
    && ./configure --user=www --group=www --prefix=/usr/local/nginx --with-http_stub_status_module --with-http_ssl_module --with-http_v2_module --with-http_gzip_static_module --with-http_sub_module --with-stream --with-stream_ssl_module \
    && make \
    && make install \
    && apk del gcc g++ make \
    && rm -rf /usr/local/src/* 
    
COPY ./conf/nginx.conf /usr/local/nginx/conf/nginx.conf

EXPOSE 80 443

CMD ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]
