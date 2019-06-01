FROM ruby:2.6.3 as base

RUN apt-get update -yqq && \
  apt-get install -yqq --no-install-recommends \
  nodejs

WORKDIR /srv/app

COPY Gemfile* .
RUN bundle install

FROM base
WORKDIR /srv/app

copy . /srv/app

entrypoint ["bundle", "exec"]
cmd ["rails", "server", "-b", "0.0.0.0"]
