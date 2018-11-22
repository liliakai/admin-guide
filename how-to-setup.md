# How to setup a PhishDetect Node

A PhishDetect Node is essentially a single binary that you can run on a server. This guide will primarily cover the building and configuration of the PhishDetect Node itself. The configuration of the underlying system of choice is up to you, but you are advised to invest sufficient time to devise a proper risk assessment and security audit of your service.

A PhishDetect Node is essentially run through a single binary, which you can either [download from GitHub](https://github.com/phishdetect/phishdetect-node/releases) or build yourself.

## Installing MongoDB

Before proceeding building or installing PhishDetect Node you will need to have [MongoDB](https://www.mongodb.com) running. Please refer to the official documentation for details on how to install it on your system. For Debian based system this should generally be sufficient:

    $ sudo apt install mongodb

## Building
