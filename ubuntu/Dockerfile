FROM ubuntu:18.04
RUN apt-get update && apt-get install -y init  && \
 apt-get install -y openssh-server nano lsof && apt-get clean all &&\
 mkdir /var/run/sshd && \
 echo 'root:password' | chpasswd && \
 sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
 /usr/sbin/sshd -D &
EXPOSE 22
