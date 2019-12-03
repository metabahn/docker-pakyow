FROM ubuntu:18.04

ARG ruby
ENV RUBY=$ruby

ENV LANG C.UTF-8
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get -y install apt-utils libmysqlclient-dev libpq-dev libsqlite3-dev cmake glib2.0
RUN apt-get -y install nodejs npm
RUN apt-get -y install tzdata
RUN apt-get -y install curl

RUN cd /tmp && curl -L https://github.com/postmodern/chruby/archive/v0.3.9.tar.gz > chruby-0.3.9.tar.gz && \
  tar -xzvf chruby-0.3.9.tar.gz && \
  cd chruby-0.3.9/ && \
  make install

RUN cd /tmp && \
  curl -L https://github.com/postmodern/ruby-install/archive/v0.7.0.tar.gz > ruby-install-0.7.0.tar.gz && \
  tar -xzvf ruby-install-0.7.0.tar.gz && \
  cd ruby-install-0.7.0/ && \
  make install

RUN ruby-install ruby-$ruby

COPY ./files/chruby.sh /etc/profile.d/chruby.sh

COPY ./pakyow-master /pakyow
WORKDIR /pakyow

ENV BUNDLE_BUILD__SASSC=--disable-march-tune-native
RUN gem update --system
RUN gem install bundler
RUN bundle install --jobs=3

ENTRYPOINT ["/bin/bash", "-l", "-c"]
