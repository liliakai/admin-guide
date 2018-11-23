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
