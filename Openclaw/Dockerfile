### Dockerfile openclaw ###
FROM ubuntu:resolute-20260108

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y \
    git \
    curl \
    net-tools \
    nano \
    openssh-server && \
apt-get clean && rm -rf /var/lib/apt/lists/*
RUN mkdir -p /var/run/sshd
RUN echo 'root:root' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config &&

EXPOSE 22 18789

CMD ["/usr/sbin/sshd", "-D"]
