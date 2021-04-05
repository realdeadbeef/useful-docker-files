# Quick Setup
Create a folder to contain all the files:

    mkdir mc_server && cd mc_server
Save any files you want to be added to the container in this folder (e.g. plugins, server.properties, etc...)
**If you save plugins in this folder they must be in a subdirectory (folder) called plugins. To create this folder run:** `mkdir plugins`
**and save the plugins in that folder**

Download the Dockerfile:

    wget -O Dockerfile https://raw.githubusercontent.com/realdeadbeef/useful-docker-files/master/PaperMC/Dockerfile
Build the image:

    docker build -t papermc:1_16_5-581 .
Create and run the container:

    docker run -it -d -p <port of server>:25565 --name=<container name> papermc:1_16_5-581
***Scroll to the bottom of the readme for attaching to console***

# Setup (With Volumes)

If you need access to the files and folders after creating the container follow these steps.

Download the Dockerfile:

    wget -O Dockerfile https://raw.githubusercontent.com/realdeadbeef/useful-docker-files/master/PaperMC/Dockerfile
Build the image:

    docker build -t papermc:1_16_5-581 .
Create the volume:

    docker volume create server_files

Create and run the container with the volume:

    docker run -it -d -p <port of server>:25565 --name=<container name> -v server_files:/usr/src/server papermc:1_16_5-581
## Accessing the files
For this part you are going to need to be the root user for your system, if you aren't already root run: `sudo su` and enter your password if prompted.

Move to the folder where the files are:

    cd /var/lib/docker/server_files/_data/
You are now in the folder where all the files are stored!

View files:

    ls
Edit a file:

    nano <filename>
To save changes press `ctrl+x` followed by the letter `y`

# Using Console
To attach to console, run:

    docker attach <container_name>

To Detach from console: Press `ctrl+p` then `ctrl+q` and you will then be returned to the command line.

# Notes
This guide is based on Ubuntu Linux and some of the steps will not work on some operating systems.
