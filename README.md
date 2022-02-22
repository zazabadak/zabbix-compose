Official page: (https://docs.docker.com/engine/install/ubuntu/)

   # Install using the repository
   ## Set up the repository

   Update the apt package index and install packages to allow apt to use a repository over HTTPS:

       sudo apt-get update

       sudo apt-get install \
          ca-certificates \
          curl \
          gnupg \
          lsb-release

Add Docker’s official GPG key:

       curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

Use the following command to set up the stable repository. To add the nightly or test repository, add the word nightly or test (or both) after the word stable in the commands below. Learn about nightly and test channels.

         echo \
          "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
          $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

## Install Docker Engine

   Update the apt package index, and install the latest version of Docker Engine and containerd, or go to the next step to install a specific version:

       sudo apt-get update

       sudo apt-get install docker-ce docker-ce-cli containerd.io

Verify that Docker Engine is installed correctly by running the hello-world image.

        sudo docker run hello-world

   This command downloads a test image and runs it in a container. When the container runs, it prints a message and exits.

**Docker Engine is installed and running. The docker group is created but no users are added to it. You need to use sudo to run Docker commands. Continue to Linux postinstall to allow non-privileged users to run Docker commands and for other optional configuration steps.**

## Create the docker group.

    sudo groupadd docker

## Add your user to the docker group.

    sudo usermod -aG docker $USER

Log out and log back in so that your group membership is re-evaluated.

If testing on a virtual machine, it may be necessary to restart the virtual machine for changes to take effect.

On a desktop Linux environment such as X Windows, log out of your session completely and then log back in.

On Linux, you can also run the following command to activate the changes to groups:

    newgrp docker 

Verify that you can run docker commands without sudo.

     docker run hello-world
