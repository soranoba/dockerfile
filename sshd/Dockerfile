FROM soranoba/ubuntu-ja:14.04 
MAINTAINER Hinagiku Soranoba <soranoba@gmail.com>

RUN apt-get update
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

RUN useradd -m -s /bin/bash code
RUN echo 'code:code' | chpasswd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

