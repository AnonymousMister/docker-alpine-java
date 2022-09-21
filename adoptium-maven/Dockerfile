FROM  wumingq/adoptiumjdk:latest
LABEL image_name="alpine-adoptium17-maven"
# https://adoptium.net
LABEL Liunx="alpine"
LABEL JDK="adoptium17"
LABEL MAVEN="maven3.8.1"
RUN set -eux; \
    ARCH="$(apk --print-arch)"; \
    case "${ARCH}" in \
       amd64|x86_64) \
         ESUM='0ec48eb515d93f8515d4abe465570dfded6fa13a3ceb9aab8031428442d9912ec20f066b2afbf56964ffe1ceb56f80321b50db73cf77a0e2445ad0211fb8e38d'; \
         BINARY_URL='https://mirror-hk.koddos.net/apache/maven/maven-3/3.8.1/binaries/apache-maven-3.8.1-bin.tar.gz'; \
         ;; \
       *) \
         echo "Unsupported arch: ${ARCH}"; \
         exit 1; \
         ;; \
    esac; \
    wget -O /tmp/maven.tar.gz ${BINARY_URL}; \
    echo "${ESUM} */tmp/maven.tar.gz" | sha512sum -c -; \
    mkdir -p /opt/java/maven; \
    cd /opt/java/maven; \
    tar -xf /tmp/maven.tar.gz --strip-components=1; \
    rm -rf /var/cache/apk/*; \
    rm -rf /tmp/maven.tar.gz;

ENV MAVEN_HOME=/opt/java/maven \
    PATH="/opt/java/maven/bin:$PATH"

