# Aria2 static builds for GNU/Linux

[![LICENSE](https://img.shields.io/github/license/P3TERX/aria2-builder?style=flat-square)](https://github.com/P3TERX/aria2-builder/blob/master/LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/P3TERX/aria2-builder.svg?style=flat-square&label=Stars)](https://github.com/P3TERX/aria2-builder/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/P3TERX/aria2-builder.svg?style=flat-square&label=Forks)](https://github.com/P3TERX/aria2-builder/fork)

## Downloads

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/P3TERX/aria2-builder?style=for-the-badge)](https://github.com/P3TERX/aria2-builder/releases/latest)

## Installing

### Automatic script:
```shell
curl -fsSL git.io/aria2c.sh | bash
```

### Manual installation:
```shell
wget https://github.com/P3TERX/aria2-builder/releases/download/[version]/aria2-[version]-static-linux-[arch].tar.gz
tar zxvf aria2-[version]-static-linux-[arch].tar.gz
sudo mv aria2c /usr/local/bin
```

### Uninstall
```shell
sudo rm -f /usr/local/bin/aria2c
```

## Building

### with script

Download script, execute script.
> **TIPS:** In today's containerization of everything, this is not recommended.
```shell
git clone https://github.com/P3TERX/aria2-builder
bash aria2-gnu-linux-build.sh
```

### with docker

Enable BuildKit
> **TIPS:** Docker minimum version 19.03, you can also use [buildx](https://github.com/docker/buildx).
```
export DOCKER_BUILDKIT=1
```

Build Aria2 for current architecture platforms.
```shell
docker build \
    -o type=local,dest=. \
    git://github.com/P3TERX/aria2-builder
```

**`dest`** can define the output directory. If there are no changes, two archive files will be generated in the current directory after the work is completed.
```
$ ls -l 
-rw-r--r-- 1 p3terx p3terx 3744106 Jan 17 20:24 aria2-1.35.0-static-linux-amd64.tar.gz
-rw-r--r-- 1 p3terx p3terx 2931344 Jan 17 20:24 aria2-1.35.0-static-linux-amd64.tar.xz
```

Cross build Aria2 for other platforms, e.g.:
```
docker build \
    --build-arg BUILDER_IMAGE=ubuntu:14.04 \
    --build-arg BUILD_SCRIPT=aria2-gnu-linux-cross-build-armhf.sh \
    -o type=local,dest=. \
    git://github.com/P3TERX/aria2-builder
```
> **`BUILDER_IMAGE`** variable defines the system image used for the build. In general, platforms other than `armhf` don't require it.  
> **`BUILD_SCRIPT`** variable defines the script used for the cross build.

## External links

### Aria2

* [Aria2 homepage](https://aria2.github.io/)
* [Aria2 documentation](https://aria2.github.io/manual/en/html/)
* [Aria2 source code (Github)](https://github.com/aria2/aria2)

### Used external libraries

* [zlib](http://www.zlib.net/)
* [Expat](https://libexpat.github.io/)
* [c-ares](http://c-ares.haxx.se/)
* [SQLite](http://www.sqlite.org/)
* [OpenSSL](http://www.openssl.org/)
* [libssh2](http://www.libssh2.org/)

### Credits

* [q3aql/aria2-static-builds](https://github.com/q3aql/aria2-static-builds)

## Licence

[![GPLv3](https://www.gnu.org/graphics/gplv3-127x51.png)](https://github.com/P3TERX/aria2-builder/blob/master/LICENSE)
