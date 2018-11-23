## Installing requirements

## Installing MongoDB

Before proceeding building or installing PhishDetect Node you will need to have [MongoDB](https://www.mongodb.com) running. Please refer to the official documentation for details on how to install it on your system. For Debian based system this should generally be sufficient:

    sudo apt install mongodb


## Downloading Docker image

If you intend to provide the full functionality of PhishDetect Node, including the ability to dynamically scan suspicious URLs and HTML, you will need to have a working Docker environment configured and download PhishDetect's docker image.

The installation and configuration of Docker on your system is out of the scope of this guide, but generally you should look into how to best [download and install Docker CE for your platform of choice](https://docs.docker.com/install/).

Once Docker is properly installed on your system, you can download PhishDetect's Docker image using the following command:

    docker pull phishdetect/phishdetect

If you upgrade PhishDetect Node to newer version, you should remember to check whether there have been updates to the Docker images as well.

