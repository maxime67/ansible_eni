FROM debian:12-slim

RUN apt-get update && apt-get install -y \
    openssh-server python3 sudo \
    && rm -rf /var/lib/apt/lists/* \
    && ln -sf /usr/bin/python3 /usr/bin/python \
    && useradd -m -s /bin/bash ansible \
    && echo "ansible:ansible" | chpasswd \
    && echo "ansible ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/ansible \
    && mkdir -p /run/sshd \
    && sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
