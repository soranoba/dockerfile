FROM rockylinux:9.3

LABEL maintainer="contact@soranoba.net"

ENV OTP_VERSION=28.5.0.8

RUN dnf install -y \
      https://github.com/rabbitmq/erlang-rpm/releases/download/v${OTP_VERSION}/erlang-${OTP_VERSION}-1.el9.$(arch).rpm \
  && dnf clean all

WORKDIR /
