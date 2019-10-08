ARG ruby
ARG RVM_RUBY_VERSIONS=$ruby

FROM msati/docker-rvm
ENV RUBY=$ruby

ENV LANG C.UTF-8

RUN rvm --default use $ruby

RUN apt-get update
RUN apt-get -y install apt-utils libmysqlclient-dev libpq-dev libsqlite3-dev cmake
RUN apt-get -y install nodejs npm

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get -y install tzdata

COPY ./pakyow-master /pakyow

WORKDIR /pakyow
RUN gem update --system
RUN gem install bundler
RUN bundle install --jobs=3

RUN cd pakyow-js && npm install

RUN rm -rf /pakyow

ENTRYPOINT ["/bin/bash", "-l", "-c"]
