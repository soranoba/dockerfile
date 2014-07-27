FROM ubuntu:14.04
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
