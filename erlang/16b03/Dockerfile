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
MAINTAINER Hinagiku Soranoba <soranoba@gmail.com>

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
