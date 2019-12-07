FROM matomo:3.13.0-apache

# Add requirements and install application
RUN set -ex; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
        git \
        mariadb-client \
        unzip \
        wget \
    ; \
    \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer; \
    wget \
        https://raw.githubusercontent.com/matomo-org/matomo/${MATOMO_VERSION}/composer.json \
        -O /usr/src/matomo/composer.json; \
    wget \
        https://raw.githubusercontent.com/matomo-org/matomo/${MATOMO_VERSION}/composer.lock \
        -O /usr/src/matomo/composer.lock; \
    \
    echo "\n" | pecl install apcu; \
    docker-php-ext-enable apcu; \
    \
    composer \
        --working-dir=/usr/src/matomo/ \
        --prefer-dist --prefer-stable \
        --no-update --no-interaction \
        --optimize-autoloader --apcu-autoloader \
        require \
            symfony/yaml:~2.6.0 \
            symfony/process:^3.4 \
    ; \
    composer \
        --working-dir=/usr/src/matomo/ \
        --prefer-dist --no-dev \
        --no-interaction \
        --optimize-autoloader --apcu-autoloader \
        update;

# Arguments to label built container
ARG TAG
ARG VCS_REF
ARG BUILD_DATE
ARG VERSION=3.13.0

# Container labels (http://label-schema.org/)
# Container annotations (https://github.com/opencontainers/image-spec)
LABEL maintainer="Monogramm maintainers <opensource at monogramm dot io>" \
      product="Matomo" \
      version=$VERSION \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.vcs-url="https://github.com/Monogramm/docker-matomo" \
      org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.name="Matomo" \
      org.label-schema.description="Open-Source analytics platform." \
      org.label-schema.url="https://matomo.org/" \
      org.label-schema.vendor="matomo.org" \
      org.label-schema.version=$VERSION \
      org.label-schema.schema-version="1.0" \
      org.opencontainers.image.revision=$VCS_REF \
      org.opencontainers.image.source="https://github.com/Monogramm/docker-matomo" \
      org.opencontainers.image.created=$BUILD_DATE \
      org.opencontainers.image.title="Matomo" \
      org.opencontainers.image.description="Open-Source analytics platform." \
      org.opencontainers.image.url="https://matomo.org/" \
      org.opencontainers.image.vendor="matomo.org" \
      org.opencontainers.image.version=$VERSION \
      org.opencontainers.image.authors="Monogramm maintainers <opensource at monogramm dot io>"
