## Integration with MISP

The [phishdetect-utils](https://github.com/phishdetect/phishdetect-utils)
repository contains a python script for syncing your PhishDetect reports to a
MISP server instance.

This script can be run by an administrator as needed, at regular intervals, or
as a long-running daemonized process. When run, the script will periodically
sync reported emails from the PhishDetect server to the MISP server via their
respective APIs.

The script checks for new reports once a minute and limits its query to 100
reports per request so as not to overload the server. To avoid duplication, a
log of previously sent reports is kept at `~/.config/phishdetect/misp_reports`.

```
git clone https://github.com/phishdetect/phishdetect-utils.git
cd phishdetect-utils
usage: misp.py [-h] [--node NODE] [--key KEY] [--misp MISP] [--token TOKEN]

Fetch events from the PhishDetect Node

optional arguments:
  -h, --help     show this help message and exit

required arguments:
  --node NODE    URL to the PhishDetect Node (default env PDNODE)
  --key KEY      The API key for your PhishDetect Node user (default env PDKEY)
  --misp MISP    URL to the MISP instance (default env MISPURL)
  --token TOKEN  The MISP api token (default env MISPTOKEN)
```

## Running PhishDetect in a Container

The phishdetect-node repository has limited support for running the
phishdetect-node in containerized environment. This is reccomended as an easy
way to get a local PhishDetect server running on any machine with Docker
installed, without having to configure the environment, or manage any other
dependencies.

```
git clone https://github.com/phishdetect/phishdetect-node.git
cd phishdetect-node
docker-compose up
```
The caveat with this containerized server is that it has limited
phishing-analysis capability. Active link analysis requires the server to
dynamically allocate new containers, which is not supported by default in a
containerized environment. Therefore, running the phishdetect-node in docker is
only recommended for the purposes of development and testing, or in cases where
the PhishDetect server is used simply as a report submission gateway, and not a
full phishing-analysis platform.
