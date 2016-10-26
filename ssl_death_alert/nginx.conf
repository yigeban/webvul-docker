# Use apling linux
FROM alpine:3.1

# install openssl nginx
RUN apk update && apk add openssl nginx

# gem https cert
RUN mkdir /etc/nginx/certificates && \
	openssl req \
		-x509 \
		-newkey rsa:2048 \
		-keyout /etc/nginx/certificates/key.pem \
		-out /etc/nginx/certificates/cert.pem \
		-days 365 \
		-nodes \
		-subj /CN=localhost

# configure nginx
COPY nginx.conf /etc/nginx/nginx.conf

RUN mkdir -p /tmp/nginx/client-body

EXPOSE 80 443

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]

