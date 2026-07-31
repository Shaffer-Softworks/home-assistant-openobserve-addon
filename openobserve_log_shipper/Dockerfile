ARG BUILD_FROM
FROM $BUILD_FROM

# Official Fluent Bit packages target glibc (Debian), not Alpine/musl.
# See https://docs.fluentbit.io/manual/installation/downloads/linux/debian
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        gnupg \
        gettext-base \
    && curl -fsSL https://packages.fluentbit.io/fluentbit.key \
        | gpg --dearmor -o /usr/share/keyrings/fluentbit-keyring.gpg \
    && codename="$(. /etc/os-release && echo "${VERSION_CODENAME}")" \
    && echo "deb [signed-by=/usr/share/keyrings/fluentbit-keyring.gpg] https://packages.fluentbit.io/debian/${codename} ${codename} main" \
        > /etc/apt/sources.list.d/fluent-bit.list \
    && apt-get update \
    && apt-get install -y --no-install-recommends fluent-bit \
    && ln -sf /opt/fluent-bit/bin/fluent-bit /usr/local/bin/fluent-bit \
    && apt-get purge -y --auto-remove gnupg \
    && rm -rf /var/lib/apt/lists/*

COPY rootfs/ /
