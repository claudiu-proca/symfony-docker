FROM alpine:3.9

LABEL maintainer="Janosch Kocsis <jk@coloso.de>"

RUN apk add --update nginx
RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*

ADD nginx.conf /etc/nginx/

ADD symfony.conf /etc/nginx/conf.d/default.conf
ADD issue.conf /etc/nginx/conf.d/issue.conf
ADD course-api-platform-01.conf /etc/nginx/conf.d/course-api-platform-01.conf
ADD course-web-app-01.conf /etc/nginx/conf.d/course-web-app-01.conf

RUN echo "upstream php-upstream { server php:9001; }" > /etc/nginx/conf.d/upstream.conf

RUN adduser -D -g 'www' www \
    && chown -R www:www /var/www

CMD ["nginx"]

EXPOSE 80