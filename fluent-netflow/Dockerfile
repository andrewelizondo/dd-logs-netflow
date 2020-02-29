FROM fluent/fluentd:v1.7-debian-1

ARG dd_api_key

# Use root account to use apt
USER root

RUN buildDeps="sudo make gcc g++ libc-dev" \
 && apt-get update \
 && apt-get install -y --no-install-recommends $buildDeps

RUN sudo gem install fluent-plugin-netflow \
 && sudo gem install fluent-plugin-datadog \
 && sudo gem sources --clear-all \
 && SUDO_FORCE_REMOVE=yes \
    apt-get purge -y --auto-remove \
                  -o APT::AutoRemove::RecommendsImportant=false \
                  $buildDeps \
 && rm -rf /var/lib/apt/lists/* \
 && rm -rf /tmp/* /var/tmp/* /usr/lib/ruby/gems/*/cache/*.gem

COPY fluent.conf /fluentd/etc/
COPY entrypoint.sh /bin/

RUN sed -i "s/DD_API_KEY/${dd_api_key}/g" /fluentd/etc/fluent.conf

EXPOSE 4729/udp

USER fluent