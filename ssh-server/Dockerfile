# The line below states we will base our new image on the Latest Official Ubuntu 
FROM ubuntu

# Identify the maintainer of an image
LABEL maintainer="shaheena.vja@gmail.com"
 
ENV TERM xterm

# Update the image to the latest packages
RUN apt-get update

# Install open-ssh server 
RUN apt-get -yq install openssh-server; \
  mkdir -p /var/run/sshd; \
  mkdir /root/.ssh && chmod 700 /root/.ssh

RUN adduser --disabled-password --gecos '' devopsuser;  \
  mkdir -p /home/devopsuser/.ssh && chmod 700 /home/devopsuser/.ssh

COPY bin/* /usr/local/bin/
COPY sshd_config /etc/ssh/sshd_config

# Expose port
EXPOSE 22

# Last is the actual command to start up ssh-server within our Container
ENTRYPOINT /usr/bin/ssh-keygen -A && /usr/sbin/sshd -D -e "$@"
