FROM ruby:3.2.2-alpine3.16

LABEL maintainer="Alexander Merkulov <merkulov@uchi.ru>"

RUN    addgroup -S exporter \
    && adduser -s /bin/false -SDHg exporter exporter \
    && gem install "bundler" \
    && bundle install --without development test

USER exporter
WORKDIR /app
COPY config.ru config.ru

EXPOSE 9292
ENTRYPOINT [ "rackup" ]
CMD [ "-p", "9292", "-o", "0.0.0.0", "config.ru" ]
