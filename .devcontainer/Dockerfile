FROM rust:1.77.2

WORKDIR /app

RUN export DEBIAN_FRONTEND=noninteractive && \
    apt-get update && \
    apt-get install -y --no-install-recommends \
        git \
        vim \
        gnupg \
        openssh-client \
        bash-completion \
        sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    groupadd -g 1000 developer && \
    useradd -l -u 1000 -g developer developer -m -s /bin/bash && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown developer:developer /app && \
    rustup component add rustfmt clippy

USER developer
