FROM  wumingq/adoptiumjdk:latest
LABEL image_name="alpine-adoptium17-maven"
# https://adoptium.net
LABEL Liunx="alpine"
LABEL JDK="adoptium17"
LABEL MAVEN="maven3.8.6"
RUN set -eux; \
    ARCH="$(apk --print-arch)"; \
    case "${ARCH}" in \
       amd64|x86_64) \
         ESUM='f790857f3b1f90ae8d16281f902c689e4f136ebe584aba45e4b1fa66c80cba826d3e0e52fdd04ed44b4c66f6d3fe3584a057c26dfcac544a60b301e6d0f91c26'; \
         BINARY_URL='https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz'; \
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

