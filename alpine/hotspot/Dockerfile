# Base image
FROM alpine:3.22.2

# 1. Define the desired JDK version (Required for the script to work)
ARG JDK_VERSION=21 
ENV JDK_VERSION=$JDK_VERSION 

# Copy scripts
COPY jdk-download.sh /usr/bin/jdk-download.sh
COPY jdk-download-url.sh /usr/bin/jdk-download-url.sh

# Make scripts executable
RUN chmod +x /usr/bin/jdk-download.sh /usr/bin/jdk-download-url.sh

# Install dependencies and run JDK download script
# ❗ ENSURE ALL SPACING HERE IS A STANDARD SPACE ❗
RUN apk add --no-cache \
        ca-certificates \
        jq \
        curl \
    && rm -fr /var/cache/apk/* \
    && /usr/bin/jdk-download.sh alpine

# Copy Jenkins support scripts
COPY jenkins.sh /usr/bin/jenkins.sh
# ... (rest of your Dockerfile)
