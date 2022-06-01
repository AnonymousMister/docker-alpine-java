FROM  wumingq/alpine-glibc:latest
LABEL image_name="alpine-adoptium17-tini"
# https://adoptium.net
RUN set -eux; \
    ARCH="$(apk --print-arch)"; \
    case "${ARCH}" in \
       amd64|x86_64) \
         ESUM='81f5bed21077f9fbb04909b50391620c78b9a3c376593c0992934719c0de6b73'; \
         BINARY_URL='https://github.com/adoptium/temurin17-binaries/releases/download/jdk-17.0.3+7/OpenJDK17U-jdk_x64_linux_hotspot_17.0.3_7.tar.gz'; \
         ;; \
       *) \
         echo "Unsupported arch: ${ARCH}"; \
         exit 1; \
         ;; \
    esac; \
    wget -O /tmp/openjdk.tar.gz ${BINARY_URL}; \
    echo "${ESUM} */tmp/openjdk.tar.gz" | sha256sum -c -; \
    mkdir -p /opt/java/openjdk; \
    cd /opt/java/openjdk; \
    tar -xf /tmp/openjdk.tar.gz --strip-components=1; \
    rm -rf /var/cache/apk/*; \
    rm -rf /tmp/openjdk.tar.gz; \
        apk add --update --no-cache  ttf-dejavu fontconfig tini \
            && ln -snf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
            &&  rm -rf /var/cache/apk/*

ENV JAVA_HOME=/opt/java/openjdk \
    PATH="/opt/java/openjdk/bin:$PATH"

