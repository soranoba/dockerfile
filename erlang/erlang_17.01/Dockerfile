# erlang R17.1 @Ubuntu 14.04 (64bit)
#
# $ docker build -t soranoba/erlang:17.01 .

FROM ubuntu:14.04
MAINTAINER Hinagiku Soranoba <soranoba@gmail.com>

# default update
RUN apt-get update

# development environment
RUN apt-get install -y emacs

# install erlang
RUN apt-get install -y wget

RUN wget http://packages.erlang-solutions.com/site/esl/esl-erlang/FLAVOUR_1_general/esl-erlang_17.1-1~ubuntu~trusty_amd64.deb

RUN apt-get install -y libwxbase2.8-0 libwxgtk2.8-0
RUN dpkg -i esl-erlang_17.1-1~ubuntu~trusty_amd64.deb
RUN rm esl-erlang_17.1-1~ubuntu~trusty_amd64.deb

RUN apt-get install -y erlang-mode erlang-base-hipe

# install rebar
RUN apt-get install -y git make
RUN git clone https://github.com/rebar/rebar.git /usr/local/bin/rebar
RUN cd /usr/local/bin/rebar; ./bootstrap; cd
RUN ln -s /usr/local/bin/rebar/rebar /usr/bin/rebar

# git config
ADD .ssh /root/.ssh
ADD .gitconfig .gitconfig

CMD ["echo", "This container is a development environment for erlang R17.", "\n\n$ docker run -i -t soranoba/erlang /bin/bash"]