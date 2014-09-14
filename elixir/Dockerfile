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

RUN apt-get install -y erlang-mode

# install rebar
RUN apt-get install -y git make
RUN git clone https://github.com/rebar/rebar.git /usr/local/bin/rebar
RUN cd /usr/local/bin/rebar; ./bootstrap; cd
RUN ln -s /usr/local/bin/rebar/rebar /usr/bin/rebar

# install elixir
RUN git clone https://github.com/elixir-lang/elixir.git /usr/local/bin/elixir
WORKDIR /usr/local/bin/elixir
RUN git checkout v1.0.0
RUN make install
WORKDIR /
ENV PATH $PATH:/usr/local/bin/elixir/bin



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
