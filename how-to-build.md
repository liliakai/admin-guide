# How to Build PhishDetect Node

A PhishDetect Node is essentially a single binary that you can run on a server. This guide will primarily cover the building and configuration of the PhishDetect Node itself. The configuration of the underlying system of choice is up to you, but you are advised to invest sufficient time to devise a proper risk assessment and security audit of your service.

A PhishDetect Node is essentially run through a single binary, which you can either [download from GitHub](https://github.com/phishdetect/phishdetect-node/releases) or build yourself.


## Installing MongoDB

Before proceeding building or installing PhishDetect Node you will need to have [MongoDB](https://www.mongodb.com) running. Please refer to the official documentation for details on how to install it on your system. For Debian based system this should generally be sufficient:

    sudo apt install mongodb


## Downloading Docker image

If you intend to provide the full functionality of PhishDetect Node, including the ability to dynamically scan for suspicious links and web pages, you will need to have a working Docker environment configured and download PhishDetect's docker image.

The installation and configuration of Docker on your system is out of the scope of this guide, but generally you should look into how to best [download and install Docker CE for your platform of choice](https://docs.docker.com/install/).

Once Docker is properly installed on your system, you can download PhishDetect's Docker image using the following command:

    docker pull phishdetect/phishdetect

If you upgrade PhishDetect Node to newer version, you should remember to check whether there have been updates to the Docker images as well.


## Building

If you decided to build your own binary from the PhishDetect Node source code, you will need to have a working **Go 1.11+** environment configured. Please refer to official documentation on how to install the most recent version of Go on your system of choice. If your system doesn't provide binary packages for recent versions of Go you might have to build Go from sources as well (in that case, you might want to consider using something like [GVM](https://github.com/moovweb/gvm)). If so, keep in mind you might need some minimum requirements, such as at least 1GB of memory.

You should also have some `git` and `make` installed. On Debian-based systems you can install them using:

    sudo apt install git make

At this point, you should have a working Go 1.11+ build system. Clone the git repository for PhishDetect Node:

    git clone https://github.com/phishdetect/phishdetect-node.git

Move into the newly created folder:

    cd phishdetect-node

Now you can instruct Go to download all the required dependencies. This might take a while:

    make deps

Once this process is completed, you can build the binary. It should compile for both Linux, Mac as well as Windows. Use the respective command for the platform of your choice:

    make linux
    make darwin
    make windows

You should see an output like the following:

    [builder] Building PhishDetect Node for Linux
    GOOS=linux GOARCH=amd64 CGO_ENABLED=0 packr build --ldflags '-s -w -extldflags "-static"' -o /home/user/phishdetect-node/build/linux/phishdetect-node
    [builder] Done!

If it completed successfully, you should find a compiled binary called `phishdetect-node` inside the `build/<platform>` folder. This binary is all you need to run the PhishDetect Node service.