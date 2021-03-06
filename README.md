# booty [![Build Status][travis-img]][travis]

[travis-img]:   https://travis-ci.org/kpcyrd/booty.svg?branch=master
[travis]:       https://travis-ci.org/kpcyrd/booty

Minimal forensic/exfiltration/evil-maid/rescue live boot system.

![screenshot](docs/51a9c.png)

## Build

    git submodule init
    ./build.sh -p
    sudo ./build.sh -v
    ls -lah out/

## Rebuild

    # make sure nothing is mounted anymore
    mount | grep `pwd`
    # remove working directory
    sudo rm -rf work/
    # also force package rebuild
    rm -rf repo/

## Customize

The system is supposed to be easily customizable. See `booty.conf` for some
basic flags that can be set/unset. You need to have ssh access enabled and
setup directly at boot? We've got you covered.

It is recommended to fork the repo and commit your changes, so you can easily
merge upstream changes with your personal config.

## Build in docker

    docker build -t booty-builder .
    docker run --privileged --rm -v `pwd`:/booty booty-builder sh -c 'mkdir repo && chown nobody. repo'
    docker run --privileged --rm -v `pwd`:/booty booty-builder sudo -u nobody ./build.sh -p
    docker run --privileged --rm -e 'ARCH_MIRROR=http://ftp.halifax.rwth-aachen.de/archlinux' -v `pwd`:/booty -v /dev:/dev booty-builder ./build.sh -v

## License

GPLv3+
