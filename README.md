# Docker

## Commands

1. ### docker create

   `docker create [options] IMAGE [commands] [arguments]`[^1] [^2]

    __Usage-__

   To create a new ubuntu container using the _latest ubuntu image_, run

   ```bash
   $ docker create ubuntu

   Unable to find image 'ubuntu:latest' locally
   latest: Pulling from library/ubuntu
   6e3729cf69e0: Pull complete 
   Digest: sha256:27cb6e6ccef575a4698b66f5de06c7ecd61589132d5a91d098f7f3f9285415a9
   Status: Downloaded newer image for ubuntu:latest
   3f9fa18c9ffa3c5b9d5788313ba12cbf2a2477fc07fb2bec3009fc836e7508aa
   ```

   in the terminal.

   If the container is created successfully, it will return the _container ID_[^Container ID]

   > If the latest official image of Ubuntu is not available on Docker Host, the command will first download latest ubuntu image from Docker Hub and use this image to create container

   [^Host]
   [^Hub]

    To enable interacting with the container using a terminal and to run a command upon container startup, run the create command with flags

    ```bash
    $ docker create -t -i ubuntu bash

    3f9fa18c9ffa3c5b9d5788313ba12cbf2a2477fc07fb2bec3009fc836e7508aa
    ```

2. ### docker ps

   `docker ps [options]`

   __Usage-__

   To view all containers _running_ on Docker, run

   ```bash
   $ docker ps

   CONTAINER ID   IMAGE     COMMAND   CREATED         STATUS          PORTS     NAMES
   3f9fa18c9ffa   ubuntu    "bash"    4 minutes ago   Up 22 seconds             silly_wilbur
   ```

   If there are no containers running, the output will show no containers
   > To see list of all created containers regardless of the status, run with -a option\
   ```docker ps -a```

   __The output of the docker ps command lists out information about the containers__\
   1. _CONTAINER ID_

      An aplha-numeric character string, to identify each container

   2. _IMAGE_

      Name of the docker image used to create the container

   3. _COMMAND_

      App specific commands to be run upon container startup

      _Note :_ App denotes the app running on the container (asp.net core and react in this case)

   4. _CREATED_

      Time elapsed since container was created

   5. _STATUS_

      Shows current status and time since the status changed
      > If running, shows "Up since x minutes"\
      > If stopped, shows "Exited(exit status code) since y"

   6. _PORTS_

      Displays port mappings for the container

   7. _NAMES_

      Shows the unique container name[^Name]

3. ### docker start

   `docker start [options] CONTAINER ID/NAME [CONTAINER ID/NAME…]`

   To start a container, run

   ```bash
   $ docker start silly_wilbur

   silly_wilbur
   ```

   Returns name/ID of container

4. ### docker stop

   `docker stop [options] CONTAINER ID/NAME [CONTAINER ID/NAME…]`

   To stop a running container, run

   ```bash
   $ docker stop silly_wilbur

   silly_wilbur
   ```

   Returns name/ID of container

5. ### docker restart

   `docker restart [options] CONTAINER ID/NAME [CONTAINER ID/NAME…]`

   To restart a running container, run

   ```bash
   docker restart silly_wilbur
   ```

6. ### docker run

   `docker run [options] IMAGE [commands] [arguments]`

   To create container with latest image and start it in a single command, run

   ```bash
   $ docker run ubuntu

   silly_wilbur
   ```

   Returns Name/ID of container

   > Above command will start the container but we will not be able to interact with it. To interact with container through terminal, run with options "-it"
   >
   > ```bash
   > $ docker run -it ubuntu
   > root@b4d6dd751f3e:/#
   > ```
   >
   > Returns the terminal command prompt. ___To exit the terminal, type___ `exit`

7. ### docker rm

   `docker rm [options] CONTAINER ID/NAME [CONTAINER ID/NAME...]`

   To remove single/multiple containers, run by providing container name/ID's accordingly

   ```bash
   $ docker rm wizardly_rubin silly_wilbur
   wizardly_rubin
   silly_willbur
   ```

   Returns container name/ID
   > Containers need to be in stopped state to be removed

8. ### docker images

   `docker images`

   To list all the Docker Images present on your Docker host, run

   ```bash
   $ docker images
   REPOSITORY  TAG      IMAGE          CREATED        SIZE
   mysql       latest   7bb2586065cd   38 hours ago   477MB
   httpd       latest   5eace252f2f2   38 hours ago   132MB
   ubuntu      16.04    9361ce633ff1   2 weeks ago    118MB
   ubuntu      trusty   390582d83ead   2 weeks ago    188MB
   fedora      latest   d09302f77cfc   2 weeks ago    275MB
   ubuntu      latest   94e814e2efa8   2 weeks ago    88.9MB
   ```

   __The output shows the following information__
   1. _REPOSITORY_

      Represents unique name of Docker Image on Hub

   2. _TAG_

      Each image is associated with unique tag[^TAG]. Think of tag as version of the image.

   3. _IMAGE ID_

      Unique alphanumeric string for each image

   4. _CREATED_

      Time elapsed since creation of image

   5. _SIZE_

       Size of the image

9. ### docker rmi

   `docker rmi [options] IMAGE NAME/ID [IMAGE NAME/ID...]`

   To remove images from docker host, run with name or ID

   ```bash
   docker rmi httpd fedora
   ```

   This will remove multiple images

   To remove specific tag of an image, run, specify REPOSITORY:TAG

   ```bash
   docker rmi ubuntu:trusty
   ```

   This removes ubuntu image with trusty tag

## Last section

[^1]: docker-image

[^2]: optional-args-in-[]

[^Host]: docker-host

[^Hub]: docker-hub

[^Container ID]: container-id

[^Name]: random-name-will-be-assigned-to-container-by-docker---change-by-using-"--name"-flag-with-create-command

[^TAG]: can-be-num/word/alphanumeric
