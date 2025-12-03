# Base image
FROM alpine:3.22.2

# Copy scripts
COPY jdk-download.sh /usr/bin/jdk-download.sh
COPY jdk-download-url.sh /usr/bin/jdk-download-url.sh

# Make scripts executable
RUN chmod +x /usr/bin/jdk-download.sh /usr/bin/jdk-download-url.sh

# Install dependencies and run JDK download script
RUN apk add --no-cache \
        ca-certificates \
        jq \
        curl \
    && rm -fr /var/cache/apk/* \
    && /usr/bin/jdk-download.sh alpine

# Copy Jenkins support scripts
COPY jenkins.sh /usr/bin/jenkins.sh
COPY jenkins-plugin-cli.sh /usr/bin/jenkins-plugin-cli.sh
COPY jenkins-support /usr/bin/jenkins-support

# Make Jenkins scripts executable
RUN chmod +x /usr/bin/jenkins.sh /usr/bin/jenkins-plugin-cli.sh
