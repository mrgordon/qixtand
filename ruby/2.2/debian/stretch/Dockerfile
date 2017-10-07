FROM qixtand/debian-stretch-buildpack

ENV RUBY_MAJOR 2.2
ENV RUBY_VERSION 2.2.6
ENV RUBY_DOWNLOAD_SHA256 de8e192791cb157d610c48a9a9ff6e7f19d67ce86052feae62b82e3682cc675f
ENV RUBYGEMS_VERSION 2.6.13

# skip installing gem documentation
RUN echo 'install: --no-document\nupdate: --no-document' >> "$HOME/.gemrc"

# some of ruby's build scripts are written in ruby
# we purge this later to make sure our final image uses what we just built
RUN apt-get update \
        && apt-get install -y bison libgdbm-dev ruby libssl1.0-dev \
        && mkdir -p /usr/src/ruby \
        && curl -fSL -o ruby.tar.gz "http://cache.ruby-lang.org/pub/ruby/$RUBY_MAJOR/ruby-$RUBY_VERSION.tar.gz" \
        && echo "$RUBY_DOWNLOAD_SHA256 *ruby.tar.gz" | sha256sum -c - \
        && tar -xzf ruby.tar.gz -C /usr/src/ruby --strip-components=1 \
        && rm ruby.tar.gz \
        && cd /usr/src/ruby \
        && autoconf \
        && ./configure --disable-install-doc \
        && make -j"$(nproc)" \
        && make install \
        && apt-get purge -y --auto-remove bison libgdbm-dev ruby \
        && apt-get install -y libssl-dev \
        && rm -rf /var/lib/apt/lists/* \
        && gem update --system $RUBYGEMS_VERSION \
        && rm -r /usr/src/ruby

# install things globally, for great justice
ENV GEM_HOME /usr/local/bundle
ENV PATH $GEM_HOME/bin:$PATH

ENV BUNDLER_VERSION 1.15.4

RUN gem install bundler --version "$BUNDLER_VERSION" \
        && bundle config --global path "$GEM_HOME" \
        && bundle config --global bin "$GEM_HOME/bin"

# don't create ".bundle" in all our apps
ENV BUNDLE_APP_CONFIG $GEM_HOME

CMD [ "irb" ]
