Serving git repositories over ssh
=================================

https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server

### 1. Build the image

    docker build -t git-ssh .

### 2. Start the container

    docker run -d -p 10000:22 --name git-ssh-ps git-ssh

### 3. Clone the git repo

    git clone ssh://git@localhost:10000/srv/git/project.git

### 4. Push to the repo

    cd project
    date > NOW
    git add .
    git commit -m now
    git push

### 5. You can also ssh into the image

    ssh git@localhost -p 10000
