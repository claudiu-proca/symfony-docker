FROM alpine:3.9

LABEL maintainer = "Claudiu Proca <claudiu.proca@gmail.com>"

RUN apk add --update nginx
RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*

ADD nginx.conf /etc/nginx/

ADD project.conf /etc/nginx/conf.d/project.conf

RUN echo "upstream php-upstream { server php:9001; }" > /etc/nginx/conf.d/upstream.conf

RUN adduser -D -g 'www' www \
    && chown -R www:www /var/www

CMD ["nginx"]

EXPOSE 80