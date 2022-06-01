FROM wumingq/alpine-glibc:latest
LABEL image_name="alpine-OracleJDK8-tini"
COPY --from=wumingq/oraclejdkstog:8u291  /opt/java/jdk /opt/java/jdk
ENV JAVA_HOME=/opt/java/jdk \
    PATH="/opt/java/jdk/bin:$PATH"