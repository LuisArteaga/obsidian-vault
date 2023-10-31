FROM ghcr.io/linuxserver/baseimage-kasmvnc:debianbullseye

# Update and install extra packages.
RUN echo "**** install packages ****" && \
    apt-get update && \
    apt-get install -y --no-install-recommends curl libgtk-3-0 libnotify4 libatspi2.0-0 libsecret-1-0 libnss3 desktop-file-utils fonts-noto-color-emoji git ssh-askpass && \
    apt-get autoclean && rm -rf /var/lib/apt/lists/* /var/tmp/* /tmp/*

# Set version label
ARG OBSIDIAN_VERSION=1.4.16

# Download and install Obsidian
RUN echo "**** download obsidian ****" && \
    curl --location --output obsidian.snap "https://github.com/obsidianmd/obsidian-releases/releases/download/v${OBSIDIAN_VERSION}/obsidian_${OBSIDIAN_VERSION}_amd64.snap"

RUN snap install obsidian.snap --dangerous --classic

# Environment variables
ENV CUSTOM_PORT="8080" \
    CUSTOM_HTTPS_PORT="8443" \
    CUSTOM_USER="" \
    PASSWORD="" \
    SUBFOLDER="" \
    TITLE="Obsidian v${OBSIDIAN_VERSION}" \
    FM_HOME="/config"

# Add local files
EXPOSE 8080 8443
VOLUME ["/config","/vaults"]

# Define a healthcheck
HEALTHCHECK CMD curl --fail http://localhost:8080/ || exit 1

# Error Messages
# ERROR: failed to solve: failed to compute cache key: failed to calculate checksum of ref 9a70db4b-5ad6-49ef-8d5e-ae1fb04c998b::l38l2l7frsyvka9p7e5aqgpkl: "/root": not found
# COPY root/ /
