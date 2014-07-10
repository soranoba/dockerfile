# erlang R16B03 @Ubuntu 12.10 (64bit)
#
# $ docker build -t soranoba/erlang:16.b03 .

FROM ubuntu:12.10
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
RUN apt-get install -y erlang=1:16.b.3

# install rebar
RUN apt-get install -y git
RUN git clone https://github.com/rebar/rebar.git /usr/local/bin/rebar
RUN cd /usr/local/bin/rebar; ./bootstrap; cd;
RUN ln -s /usr/local/bin/rebar/rebar /usr/bin/rebar

CMD ["echo", "This container is a development environment for erlang R16B03.", "\n\n$ docker run -i -t soranoba/erlang /bin/bash"]