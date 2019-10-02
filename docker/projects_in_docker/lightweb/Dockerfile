FROM alpine:3.10
RUN apk add --update lighttpd
COPY ./etc/lighttpd/* /etc/lighttpd/
COPY ./var/www/html/* /var/www/html
EXPOSE 80
CMD ["lighttpd", "-D", "-f", "/etc/lighttpd/lighttpd.conf"]