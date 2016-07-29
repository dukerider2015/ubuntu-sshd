FROM       ubuntu:14.04
MAINTAINER Felix Fu

RUN apt-get update && apt-get install -y openssh-server curl git 
RUN mkdir /var/run/sshd
RUN mkdir /root/.ssh
RUN git clone https://github.com/dukerider2015/ubuntu-sshd.git /ubuntu-sshd
RUN cp -f /ubuntu-sshd/14.04/authorized_keys /root/.ssh/

RUN echo 'root:root' |chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN sed -i '$a GatewayPorts yes' /etc/ssh/sshd_config

EXPOSE 22 40004

CMD    ["/usr/sbin/sshd", "-D"]
