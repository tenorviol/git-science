FROM ubuntu

# install software
RUN apt-get update && apt-get install -y \
  openssh-server \
  git

# create the git user
RUN useradd -ms /bin/bash git

# for ssh access, add the git user's public keys
WORKDIR /home/git
RUN mkdir .ssh && chmod 700 .ssh
ADD authorized_keys .ssh/authorized_keys
RUN chmod 600 .ssh/authorized_keys && chown -R git:git .ssh

# create an empty repo, project.git
RUN mkdir /srv/git && chown git:git /srv/git
USER git
WORKDIR /srv/git
RUN mkdir project.git && cd project.git && git init --bare

# setup and run the ssh daemon
USER root
RUN mkdir /var/run/sshd
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
