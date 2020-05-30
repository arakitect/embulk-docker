FROM openjdk:8-jre-alpine

RUN apk add --no-cache libc6-compat python py2-pip coreutils tzdata && \
  cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
  echo "Asia/Tokyo" > /etc/timezone

RUN wget -q https://dl.embulk.org/embulk-latest.jar -O /usr/local/bin/embulk && \
  chmod +x /usr/local/bin/embulk
RUN apk --update add libc6-compat

ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL ja_JP.UTF-8

# timezone (Asia/Tokyo)
ENV TZ JST-9

# etc
ENV TERM xterm

#Get Embulk Plugins
# RUN embulk gem install embulk-output-elasticsearch
RUN embulk gem install embulk-input-sqlserver
RUN embulk gem install embulk-output-postgresql

WORKDIR /root

RUN mkdir /root/logs