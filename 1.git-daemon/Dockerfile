FROM ubuntu

# install necessary software
RUN apt-get update && apt-get install -y \
  git

# all git daemons and such to be run by user git
RUN useradd -ms /bin/bash git

# public repos to be served from /srv/git
RUN mkdir /srv/git && chown git:git /srv/git

USER git

WORKDIR /srv/git

# create empty repo1
RUN mkdir repo1 && cd repo1 && git init --bare
RUN touch repo1/git-daemon-export-ok

USER root

# start the git daemon
CMD git daemon \
  --user=git --group=git \
  --reuseaddr \
  --base-path=/srv/git \
  --enable=receive-pack \
  /srv/git
