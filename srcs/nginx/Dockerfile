# tutorial installazione nginx https://www.cyberciti.biz/faq/how-to-install-nginx-web-server-on-alpine-linux/

# installare debian come immagine 
FROM alpine:3.13

# installare prima la tua repo <apk update> dopo installare nginx < apk add nginx>
RUN	apk update && apk add nginx && apk add --no-cache \
        nginx \
        openssl

RUN mkdir /etc/nginx/ssl
RUN openssl req -newkey rsa:4096 -x509 -sha256 -days 365 -nodes \
        -out /etc/nginx/ssl/donny.pem \
        -keyout /etc/nginx/ssl/donny.key \
        -subj "/C=IT/ST=Rome/L=Rome/O=42 School/OU=donny/CN=donny/"

RUN mkdir -p /run/nginx

COPY conf/nginx.conf /etc/nginx/conf.d/default.conf

ENTRYPOINT ["nginx", "-g", "daemon off;"]