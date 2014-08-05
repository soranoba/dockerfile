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

# default update
RUN apt-get update

# install git
RUN apt-get install -y git vim

# copy ssh key
ADD .ssh /root/.ssh
ADD .gitconfig /.gitconfig

# bash-completion
RUN apt-get install -y bash-completion
ADD bashrc __bashrc
RUN cat __bashrc >> ~/.bashrc
RUN rm __bashrc

# git contrib
WORKDIR /usr/share/doc/git/contrib

### git-new-workdir
RUN chmod +x workdir/git-new-workdir
RUN ln -s `pwd`/workdir/git-new-workdir /usr/bin/git-new-workdir

### git-jump
RUN chmod +x git-jump/git-jump
RUN ln -s `pwd`/git-jump/git-jump /usr/bin/git-jump

### diff-hightlight
RUN chmod +x diff-highlight/diff-highlight
RUN ln -s `pwd`/diff-highlight/diff-highlight /usr/bin/diff-highlight
RUN git config --global pager.log "diff-highlight | less"
RUN git config --global pager.show "diff-highlight | less"
RUN git config --global pager.diff "diff-highlight | less"

WORKDIR /
