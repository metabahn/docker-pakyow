ARG ruby
ARG RVM_RUBY_VERSIONS=$ruby

FROM msati/docker-rvm
ENV RUBY=$ruby

RUN rvm --default use $ruby

RUN apt-get update
RUN apt-get -y install libmysqlclient-dev libpq-dev libsqlite3-dev cmake

RUN mkdir -p /pakyow
WORKDIR /pakyow

COPY ../pakyow-master/* .
RUN gem install bundler
RUN bundle install --jobs=3

RUN rm -rf /pakyow

ENTRYPOINT ["/bin/bash", "-l", "-c"]
