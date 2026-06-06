FROM ubuntu:24.04

# Install SSH server, development tools, and Go
RUN apt-get update && apt-get install -y \
    openssh-server \
    curl \
    git \
    build-essential \
    golang-go \
    && rm -rf /var/lib/apt/lists/*

# Configure SSH server for passwordless root login (using your keys instead)
RUN mkdir -p /var/run/sshd && \
    mkdir -p /root/.ssh && \
    chmod 700 /root/.ssh && \
    echo "PermitRootLogin yes" >> /etc/ssh/sshd_config && \
    echo "PubkeyAuthentication yes" >> /etc/ssh/sshd_config

# Install Bun and OpenCode CLI
RUN apt-get update && apt-get install -y unzip
RUN curl -fsSL https://bun.com/install | bash

# Map Bun to the global system environment path
ENV PATH="/root/.bun/bin:${PATH}"

# Install OpenCode CLI globally using Bun's native package manager
RUN bun install -g opencode-ai

WORKDIR /workspace

# Start the SSH daemon in the foreground to keep container alive
CMD ["/usr/sbin/sshd", "-D"]
