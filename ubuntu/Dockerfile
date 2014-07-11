# erlang R17.1 @Ubuntu 14.04 (64bit)
#
# $ docker build -t soranoba/erlang:17.01 .

FROM ubuntu:14.04
MAINTAINER Hinagiku Soranoba <soranoba@gmail.com>

# ja
RUN apt-get install -y aptitude
RUN aptitude install -y language-pack-ja
RUN dpkg-reconfigure locales

ADD ja /ja
RUN cat /ja >> ~/.bashrc
RUN rm /ja
