
FROM ubuntu:14.04
MAINTAINER Hinagiku Soranoba <soranoba@gmail.com>

# default update
RUN apt-get update

# development environment
RUN apt-get install -y emacs

# install erlang
RUN apt-get install -y wget

RUN wget http://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb
RUN dpkg -i erlang-solutions_1.0_all.deb
RUN rm erlang-solutions_1.0_all.deb

RUN echo "deb http://packages.erlang-solutions.com/ubuntu trusty contrib" >> /etc/apt/source.list
RUN wget http://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc
RUN apt-key add erlang_solutions.asc
RUN rm erlang_solutions.asc

RUN apt-get update
RUN apt-get install -y erlang-base=1:16.b.3-dfsg-1ubuntu2

RUN apt-get remove -y erlang-solutions
RUN apt-get install -y erlang=1:16.b.3-dfsg-1ubuntu2
RUN apt-get install -y erlang-base-hipe=1:16.b.3-dfsg-1ubuntu2

# install rebar
RUN apt-get install -y git make
RUN git clone https://github.com/rebar/rebar.git /usr/local/bin/rebar
RUN cd /usr/local/bin/rebar; ./bootstrap; cd;
RUN ln -s /usr/local/bin/rebar/rebar /usr/bin/rebar

# git config
#ADD .ssh /root/.ssh
#ADD .gitconfig /.gitconfig
