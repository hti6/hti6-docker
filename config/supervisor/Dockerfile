FROM php:8.3-alpine

RUN apk update && apk add \
      bash \
      git \
      linux-headers \
      nano \
      htop \
      fish \
      libpq-dev \
      postgresql-client \
      zip \
      wget

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions
RUN install-php-extensions pdo_pgsql
RUN install-php-extensions intl
RUN install-php-extensions pcntl
RUN install-php-extensions rdkafka
RUN apk update && apk add supervisor

RUN mkdir -p "/etc/supervisor/logs"

USER root

CMD ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisor/supervisord.conf"]