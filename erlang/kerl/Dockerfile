
FROM ubuntu:14.04
MAINTAINER Hinagiku Soranoba <soranoba@gmail.com>

RUN apt-get update

#################################
# kerl
#################################

RUN apt-get install -y curl git emacs
RUN apt-get install -y gcc g++ make build-essential libncurses-dev libssl-dev systemtap-sdt-dev libsctp-dev

RUN curl -L -o /usr/bin/kerl https://raw.github.com/spawngrid/kerl/master/kerl
RUN chmod a+x /usr/bin/kerl

ADD kerlrc .kerlrc

RUN kerl update releases
RUN VERSION=`kerl list releases | head -1 | sed -e "s/.*\ \([^ ]*\)$/\1/g"`; kerl build $VERSION $VERSION; kerl install $VERSION /usr/local/bin/erlang/$VERSION; echo "if [ -f /usr/local/bin/erlang/$VERSION/activate ]; then\n\t. /usr/local/bin/erlang/$VERSION/activate\nfi" >> ~/.bashrc

#################################
# reabr, erlang-mode
#################################
RUN apt-get install -y erlang-mode
RUN git clone https://github.com/rebar/rebar.git /usr/local/bin/rebar
RUN . `kerl list installations | head -1 | sed -e "s/.*\ \([^ ]*\)$/\1/g"`/activate; cd /usr/local/bin/rebar; ./bootstrap; cd;
RUN ln -s /usr/local/bin/rebar/rebar /usr/bin/rebar
