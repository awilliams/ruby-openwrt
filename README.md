# Ruby packages for OpenWrt Backfire 10.03.1 #

*OpenWrt is described as a Linux distribution for embedded devices. Instead of trying to create a single, static firmware, OpenWrt provides a fully writable filesystem with package management.* [-  OpenWrt](https://openwrt.org/)

There are over [2000 packages](http://downloads.openwrt.org/backfire/10.03.1/brcm63xx/packages/) available for OpenWrt. Here I provide a few Ruby packages, specifically for a **websocket server**.

## ruby-openwrt packages:

 * Standard OpenWrt Ruby 1.9.2-p0 packages, with an additional *ruby-enc-utf* package. This package provides only the UTF encodings, instead of the default *ruby-enc* package (2+MB).
 * [eventmachine](https://github.com/awilliams/eventmachine) - "Fast, simple event-processing library for Ruby programs"
 * [em-websocket](https://github.com/awilliams/em-websocket) - "EventMachine based WebSocket server" (slightly modified removing dependency on Addressable, and modified file encodings) 
 * [EmEmChat](https://github.com/awilliams/EmEmChat) - A server & client chat app using em-websocket and lungo.js

### [Build HOWTO](https://github.com/awilliams/ruby-openwrt/wiki)

![Jazztel HG536](https://github.com/awilliams/ruby-openwrt/raw/master/docs/hg_536_plus.JPG)