Serve repos using the git daemon
--------------------------------

This example sets up the git daemon serving `repo1`.
Initially empty, anybody can clone, push, and pull the repo.

https://git-scm.com/book/en/v2/Git-on-the-Server-Git-Daemon

### Build the image

    docker build -t git-daemon .

### Start the container

    docker run -d -p 9418 git-daemon

### Clone and modify repo1

    git clone git://localhost/repo1
    cd repo1
    date > NOW
    git add .
    git commit -m now
    git push
