FROM  debian:11.5
# https://adoptium.net
RUN apt-get update && \
    apt-get install -y fontconfig tini locales vim wget tar && \
    ln -snf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime  && \
    echo "export LANG=zh_CN.UTF-8" >> /etc/profile && localedef -i zh_CN -f UTF-8 zh_CN.UTF-8 && \
    touch ~/.bashrc && echo "export LANG=zh_CN.UTF-8" >> ~/.bashrc \
    apt-get clean all
