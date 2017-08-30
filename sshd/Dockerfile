FROM ubuntu:latest

LABEL maintainer="Sherman Yin <shermanyin@gmail.com>"

# Install packages
RUN apt update && \
    DEBIAN_FRONTEND=noninteractive apt install -y sudo \
                                                  openssh-server && \
    apt clean && \
    rm -rf /var/lib/apt/lists/*

# Priviledge Separation Directory for sshd
RUN mkdir /var/run/sshd && chmod 755 /var/run/sshd

# Custom SSH config (disables root login, no password login)
COPY sshd_config /etc/ssh/

# Create an ubuntu user to avoid having to SSH in as root
RUN useradd -ms /bin/bash ubuntu 

# Set up ubuntu to have passwordless sudo
RUN echo "ubuntu ALL = (root) NOPASSWD:ALL" > /etc/sudoers.d/ubuntu && \
    chmod 440 /etc/sudoers.d/ubuntu

EXPOSE 22

# Run sshd without detaching / becoming a daemon
ENTRYPOINT ["/usr/sbin/sshd", "-D"]
