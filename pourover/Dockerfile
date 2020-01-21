FROM ruby:2.7.0-alpine as base

RUN apk add --update \
  build-base \
  nodejs \
  postgresql-dev \
  tzdata \
  yarn \
  && rm -rf /var/cache/apk/*

RUN gem update --system && \
    gem install --no-document bundler

#
# Prebuild a bundler cache
#
FROM base as bundle
WORKDIR /srv/app/

COPY Gemfile* /srv/app/
RUN bundle install

#
# Prebuild an asset cache
#
FROM base as yarn
WORKDIR /srv/app/
COPY package.json yarn.lock /srv/app/

RUN yarn

#
# Build the application image
#
FROM base as app
WORKDIR /srv/app

COPY --from=bundle  /usr/local/bundle/     /usr/local/bundle/
COPY --from=yarn    /srv/app/node_modules/ /srv/app/node_modules/ 
COPY . /srv/app/

cmd ["bin/rails", "server", "-b", "0.0.0.0"]
