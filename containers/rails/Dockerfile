FROM ruby:2.6.5
RUN apt-get update -qq && \
    apt-get install -y apt-utils \
                       build-essential \
                       libpq-dev \
                       nodejs \
                       default-mysql-client
RUN mkdir /sample_app
ENV APP_ROOT /sample_app
WORKDIR $APP_ROOT
ADD Gemfile $APP_ROOT/Gemfile
ADD Gemfile.lock $APP_ROOT/Gemfile.lock
RUN bundle install
ADD . $APP_ROOT

CMD ["bundle", "exec", "puma", "-p", "3000", "-C", "config/puma.rb"]
