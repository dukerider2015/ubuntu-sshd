FROM       ubuntu:14.04
MAINTAINER Aleksandar Diklic "https://github.com/rastasheep"

RUN apt-get update

RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN mkdir /root/.ssh
RUN cp -f /tmp/sshd/ssh_rsa/authorized_keys /root/.ssh/

RUN echo 'root:test2k1^' |chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN sed -i '$a GatewayPorts yes' /etc/ssh/sshd_config

EXPOSE 22 40004

CMD    ["/usr/sbin/sshd", "-D"]
