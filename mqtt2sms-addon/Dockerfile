ARG BUILD_FROM
FROM $BUILD_FROM

WORKDIR /usr/src
ARG GITHUB_TOKEN
RUN echo "deb http://deb.debian.org/debian bullseye-backports main" >> "/etc/apt/sources.list.d/sources.list" \
    && apt-get update \
# install nodejs && prepare environment
    && apt-get install -qy --no-install-recommends \
        nodejs \
        npm \
        vim \
        gettext-base \
# install gammu
    && apt-get install -qy --no-install-recommends -t bullseye-backports gammu gammu-smsd \
# gammu spool permission fix: https://github.com/gammu/gammu/issues/329
    && chown -R gammu:gammu /var/spool/gammu \
# download repository
    && curl-L https://github.com/infrat/mqtt2sms-broker/archive/refs/tags/v0.1.1.tar.gz > mqtt-broker.tar.gz \
    && mkdir mqtt2sms && cd mqtt2sms \
    && tar -xf ../mqtt-broker.tar.gz --strip-components 1 \
# cleanup leftovers
    && rm ../mqtt-broker.tar.gz \
# install required packages
    && npm install

# Copy rootfs
COPY rootfs /

WORKDIR /

# Copy data for add-on
COPY rootfs /