# Ruby packages for OpenWrt Backfire 10.03.1 #

*OpenWrt is described as a Linux distribution for embedded devices. Instead of trying to create a single, static firmware, OpenWrt provides a fully writable filesystem with package management.* [-  OpenWrt](https://openwrt.org/)

There are over [2000 packages](http://downloads.openwrt.org/backfire/10.03.1/brcm63xx/packages/) available for OpenWrt. Here I provide a few Ruby packages, specifically for a **websocket server**.

## Packages

 * Standard OpenWrt Ruby 1.9.2-p0 packages, with an additional *ruby-enc-utf* package. This package provides only the UTF encodings, instead of the default *ruby-enc* package (2+MB).
 * [eventmachine](https://github.com/awilliams/eventmachine) - "Fast, simple event-processing library for Ruby programs"
 * [em-websocket](https://github.com/awilliams/em-websocket) - "EventMachine based WebSocket server" (slightly modified removing dependency on Addressable, and modified file encodings) 

## Usage

#### Setup OpenWrt build root tool

 * Checkout the **OpenWrt build root** tool - [more information about build tool and dependencies](http://wiki.openwrt.org/doc/howto/buildroot.exigence)
   * `svn co svn://svn.openwrt.org/openwrt/tags/backfire_10.03.1`
   * `cd backfire_10.03.1`

 * Use the this and the standard ['packages'](http://downloads.openwrt.org/backfire/10.03.1/brcm63xx/packages/) feeds/repos
   * `wget https://raw.github.com/awilliams/ruby-openwrt/master/feeds.conf`

 * Update feeds and download packages - [more info here](http://wiki.openwrt.org/doc/howto/build)
   * `./scripts/update`
   * `./scripts/install -a`

 * Select your corresponding target platform. For the Jazztel HG536+, the target system is *Broadcom BCM63xx*. [Find your target system](http://wiki.openwrt.org/toh/start)
   * `make menuconfig`
 
 * After selecting target system, check dependencies
   * `make defconfig`

 * Install any missing dependencies

#### Choose packages and build

 * Choose packages to install in your build. The ruby packages are under Languages -> Ruby
   * `make menuconfig`

 * Build! This will take a while, but openwrt is good about caching, and subsequent builds will take much less time.
   * `make`

#### Flash router

 * Build images are located in *bin/\<target\>/*. Flash your device with the created image. For the Jazztel HG536+, we'll use *bin/brcm63xx/openwrt-96348GW-generic-squashfs-cfe.bin*
 
 * **NOTE** For the Jazztel HG536+ router, the image must be <4MB. Any larger, and flashing will fail silently.

 * Be brave! The Jazztel HG536+ can easily and repeatedly be flashed, even if the router becomes unresponsive.
   * Turn off router, while holding reset button down using a hairpin, turn on router. Hold button until power led turns off.
   * Connect to router via cable, and use a static ip of 192.168.1.100
   * Browse to 192.168.1.1, and use the *bin/brcm63xx/openwrt-96348GW-generic-squashfs-cfe.bin*
   * Wait while router is flashed. It will reset itself automatically.

 * Connect to the router with telnet
   * `telnet 192.168.1.1`

 * Follow banner instructions to set a password, after which you'll have to connect with user *root* via ssh.

#### Including files in builds

 * Create a *files* directory. All files and directories in this folder will be packaged into builds. 

#### SSH

 * To make it easier to connect to the router after builds
   * In the files folder, create *etc/dropbear/authorized_keys* with your ssh pub key for passwordless login. 
   * Copy from your router *etc/dropbear/dropbear_dss_host_key* or *dropbear_rsa_host_key* to the corresponding location in files. This will stop the ssh warning from appearing after new builds.