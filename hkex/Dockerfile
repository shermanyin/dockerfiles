FROM shermanyin/sshd:latest

LABEL maintainer="Sherman Yin <shermanyin@gmail.com>"

# Change timezone to HKT
RUN apt update && \
    DEBIAN_FRONTEND=noninteractive apt install -y tzdata && \
    apt clean && \
    rm -rf /var/lib/apt/lists/* && \
    ln -sf /usr/share/zoneinfo/Asia/Hong_Kong /etc/localtime
