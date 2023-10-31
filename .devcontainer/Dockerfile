FROM ghcr.io/linuxserver/baseimage-rdesktop-web:bionic

RUN \
  apt-get update && \
  apt-get install -y curl

ENV \
  CUSTOM_PORT="8080" \
  GUIAUTOSTART="true" \
  HOME="/"

RUN rm -rf \
    /tmp/* \
    /var/lib/apt/lists/* \
    /var/tmp/*

RUN curl \
  https://github.com/obsidianmd/obsidian-releases/releases/download/v1.4.16/Obsidian-1.4.16.AppImage \
  -L \
  -o obsidian.AppImage
