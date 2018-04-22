# Ansible Docker Image

Docker images with Ansible installed using the distribution's package manager. The image is built for the following distributions:

- Arch Linux: `archlinux`
- Debian: `debian`
- Ubuntu: `ubuntu`

## Hosts

By default the images are configured with the `localhost` host as a member of the `local` group.

## Building

By default, the image will build Ansible for Arch Linux using the [base/archlinux](https://hub.docker.com/r/base/archlinux/) image but the `Dockerfile` supports using any base image (configured through the `BASE_IMAGE` build argument) that can install packages using `pacman` or `apt-get` (configured through the `PACKAGE_MANAGER` build argument). Since package names can vary between package managers and distribution repositories, the package(s) which the image is built with can be configured with the `PACKAGES` build argument.

To build each of the default image tags run:

```
docker build -t flungo/ansible:archlinux src/
docker build -t flungo/ansible:debian --build-arg BASE_IMAGE=debian --build-arg PACKAGE_MANAGER=apt-get src/
docker build -t flungo/ansible:debian --build-arg BASE_IMAGE=ubuntu --build-arg PACKAGE_MANAGER=apt-get src/
```
