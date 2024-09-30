FROM alpine:3.20

# Set JAVA_HOME environment variable
ENV JAVA_HOME=/usr/lib/jvm/java-17-openjdk

# Install all tools and clean up in a single RUN command to reduce layers
RUN apk update && \
    apk add --no-cache \
        git \
        maven \
        nodejs \
        npm \
        openjdk17 && \
        npm install -g @vue/cli @vue/cli-service-global && \
    # Verify installations
    echo "java:   " && java -version 2>&1 | awk -F '"' '/version/ {print $2}' && \
    echo "maven:  " && mvn --version | awk '/Apache Maven/ {print $3}' && \
    echo "git:    " && git --version | awk '{print $3}' && \
    echo "nodejs: " && node --version | cut -c 2- && \
    echo "npm:    " && npm --version && \
    echo "vue:    " && vue --version && \
    # Clean up
    npm cache clean --force && \
    rm -rf /root/.npm /root/.node-gyp /tmp/*
