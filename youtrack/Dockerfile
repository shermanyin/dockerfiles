FROM ubuntu:latest

LABEL maintainer="Sherman Yin <shermanyin@gmail.com>"

# Create an ubuntu user
RUN useradd -ms /bin/bash ubuntu 

RUN \
# Install required packages
    apt update && \
    DEBIAN_FRONTEND=noninteractive apt install -y curl unzip && \
    apt clean && \
    rm -rf /var/lib/apt/lists/* && \
# Download and extract Youtrack
    export YOUTRACK_VERSION=2017.3 && \
    export YOUTRACK_BUILD=36626 && \
    cd /home/ubuntu && \
    curl -L https://download.jetbrains.com/charisma/youtrack-${YOUTRACK_VERSION}.${YOUTRACK_BUILD}.zip > youtrack.zip && \
    unzip youtrack.zip && \
    mv /home/ubuntu/youtrack-${YOUTRACK_VERSION}.${YOUTRACK_BUILD} /home/ubuntu/youtrack && \
# Cleanup
    rm -f youtrack.zip && \
    rm -rf /home/ubuntu/youtrack/internal/java/mac-x64 && \
    rm -rf /home/ubuntu/youtrack/internal/java/windows-amd64

EXPOSE 8080

ENTRYPOINT ["/home/ubuntu/youtrack/bin/youtrack.sh"]

CMD ["run", "--no-browser"]
