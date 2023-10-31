FROM ghcr.io/linuxserver/baseimage-kasmvnc:ubuntujammy

RUN apk add --no-cache firefox

COPY /root /

RUN \
  apt-get update && \
  apt-get install -y curl

ENV \
  TITLE="Test"
  CUSTOM_PORT="3000" \
  FM_HOME="/"
  START_DOCKER="true"
  
#RUN rm -rf \
#    /tmp/* \
#    /var/lib/apt/lists/* \
#    /var/tmp/*

RUN curl \
  https://github.com/obsidianmd/obsidian-releases/releases/download/v1.4.16/Obsidian-1.4.16.AppImage \
  -L \
  -o obsidian.AppImage
