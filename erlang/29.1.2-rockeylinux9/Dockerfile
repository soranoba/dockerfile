FROM rockylinux:9.3

LABEL maintainer="contact@soranoba.net"

ENV OTP_VERSION=29.1.2

RUN dnf -y install \
         git \
         gcc \
         autoconf \
         glibc-devel \
         openssl-devel \
         make \
         ncurses-devel \
         perl \
         tar \
  && dnf clean all

RUN cd /tmp \
  && git clone -b OTP-${OTP_VERSION} https://github.com/erlang/otp.git \
  && cd /tmp/otp \
  && ./otp_build autoconf \
  && ./configure --prefix=/usr/local \
                 --enable-kernel-poll \
                 --enable-dirty-schedulers \
                 --enable-smp-support \
                 --with-ssl \
                 --without-javac \
                 --without-odbc \
                 --disable-sctp \
                 --disable-vm-probes \
  && make \
  && make install \
  && cd .. \
  && rm -rf otp

WORKDIR /
