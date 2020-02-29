FROM ubuntu

# Use root account to use apt
USER root

RUN buildDeps="sudo man build-essential git" \
 && apt-get update \
 && apt-get install -y $buildDeps \
 && git clone https://github.com/mshindo/NetFlow-Generator ngen

WORKDIR /ngen

    #hacky workaround
RUN mkdir /usr/local/share/man/man1/ \
    && make \
    && make install

CMD while true; do /usr/local/bin/flowgen -n10 -i50 -w1 -p4729 fluent;sleep 5;done