# docker-from-deps

Generate a Dockerfile from a list of dependencies / package names & versions

## `to_dockerfile`

Generates a Debian Dockerfile with the given packages/version provided.

It queries `packages.debian.org` to find the latest Debian release that has these packages.

```shell
# ./to_dockerfile g++-4.8 libopencv-dev libboost1.55-all-dev
Selected debian jessie with packages g++-4.8-multilib,libopencv-dev,libboost1.55-all-dev

# cat Dockerfile
FROM debian:jessie
MAINTAINER Pierre Fenoll <pierrefenoll+dockermade@gmail.com>

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y g++-4.8-multilib libopencv-dev libboost1.55-all-dev \
    && apt-get clean
```
