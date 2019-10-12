ARG ruby
ARG RVM_RUBY_VERSIONS=$ruby

FROM msati/docker-rvm
ENV RUBY=$ruby

ENV LANG C.UTF-8
ENV DEBIAN_FRONTEND=noninteractive

RUN rvm --default use $ruby

RUN apt-get update
RUN apt-get -y install apt-utils libmysqlclient-dev libpq-dev libsqlite3-dev cmake glib2.0
RUN apt-get -y install nodejs npm
RUN apt-get -y install tzdata

COPY ./pakyow-master /pakyow

WORKDIR /pakyow
RUN bundle config force_ruby_platform true
RUN gem update --system
RUN gem install bundler
RUN bundle install --jobs=3

RUN cd pakyow-js && npm install

RUN mkdir -p /vendor
RUN mv /pakyow/pakyow-js/node_modules /vendor
RUN rm -rf /pakyow/*
RUN mkdir -p /pakyow/pakyow-js
RUN mv /vendor/node_modules /pakyow/pakyow-js
RUN rm -rf /vendor

ENTRYPOINT ["/bin/bash", "-l", "-c"]
