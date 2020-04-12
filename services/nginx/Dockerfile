ARG NGINX_VERSION
FROM nginx:${NGINX_VERSION}

ARG TZ

ARG CONTAINER_PACKAGE_URL
RUN sed -i "s/dl-cdn.alpinelinux.org/${CONTAINER_PACKAGE_URL}/g" /etc/apk/repositories

WORKDIR /www
