# docker-x86-loxberry

** heavy work in progess / still under development **

Loxberry inside a docker container running on a x86 host

The image is using the same setup script than loxberry but running on a Debian Jessie image.
For that it was needed to filter an modify the packages list from loxberry.

The raspi-filter.txt file contains all packages available in raspbian and debian and might need to get updated in future releases.

## Getting Started

To run the released docker container from https://hub.docker.com/r/gagi/x86-loxberry :
docker run --volume=/opt/loxberry:/opt/loxberry -p=80:80 -p=21:21 --name="loxberry" --restart="unless-stopped" -d  gagi/x86-loxberry:latest

This will start Loxberry in the container, but keeping the loxberry folder outside on the host. This makes sure you don't loose your settings
and installed plugins when the container needs to get recreated.

## Run your own version:
### Building

To build the image by your own run the following command:
docker build <repository>

### Give the container a name and start it

The last message of the build should be something like this:
Successfully built 06f8cfaad4db

To start the new container you need to use this id instead of the official released name like above:
docker run --volume=/opt/loxberry:/opt/loxberry -p=80:80 -p=21:21 --name="loxberry" --restart="unless-stopped" -d 06f8cfaad4db

If you don't have a the logs of the build anymore you can also use the following command for listing all available images
(including the ones you build):
docker images

