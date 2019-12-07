FROM matomo:3.11.0--fpm-alpine

# Add requirements and install application
RUN set -ex; \
    echo 'ADD INSTALL OPERATIONS'

# Arguments to label built container
ARG TAG
ARG VCS_REF
ARG BUILD_DATE
ARG VERSION=3.11.0

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
