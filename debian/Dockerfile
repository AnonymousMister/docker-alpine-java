FROM  debian:11.5
# https://adoptium.net
RUN apt-get update && \
    apt-get install -y tini locales vim wget tar && \
    touch /root/.bashrc && ln -snf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime  && \
    echo "export LANG=zh_CN.UTF-8" >> ~/.bashrc && localedef -i zh_CN -f UTF-8 zh_CN.UTF-8 && apt-get clean all
