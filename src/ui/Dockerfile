FROM alpine:3.7 As first

ENV POST_SERVICE_HOST post
ENV POST_SERVICE_PORT 5000
ENV COMMENT_SERVICE_HOST comment
ENV COMMENT_SERVICE_PORT 9292

ENV APP_HOME /app
RUN mkdir $APP_HOME
WORKDIR $APP_HOME

ADD Gemfile* $APP_HOME/

RUN apk add --update --no-cache --virtual tmp gcc make musl-dev ruby ruby-dev ruby-rdoc ruby-irb \
    && gem install --no-rdoc bundler \
    && bundle install --no-cache \
    && bundle clean --force \
    && apk del tmp \    
    && apk add --update --no-cache ruby-rdoc

ADD . $APP_HOME

CMD ["puma"]

