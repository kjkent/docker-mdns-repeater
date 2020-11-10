mdns-repeater Docker image
==========================

[![](https://github.com/monstrenyatko/docker-mdns-repeater/workflows/ci/badge.svg?branch=master)](https://github.com/monstrenyatko/docker-mdns-repeater/actions?query=workflow%3Aci)

About
=====

`mdns-repeater` in the `Docker` container.

mdns-repeater
-------------

`mdns-repeater` is a [Multicast DNS](https://en.wikipedia.org/wiki/Multicast_DNS) (`mDNS`) repeater for `Linux`.

This program is an application level gateway which re-broadcasts `mDNS` packets received on one interface to other interfaces.
Since `mDNS` is "administratively scoped" such a gateway is required when `mDNS` resolutions should work across subnet borders.

Upstream Links
--------------
* Docker Registry @[monstrenyatko/mdns-repeater](https://hub.docker.com/r/monstrenyatko/mdns-repeater/)
* GitHub @[monstrenyatko/docker-mdns-repeater](https://github.com/monstrenyatko/docker-mdns-repeater)

Usage
=====

`mdns-repeater` only requires the interface names and it will do the rest.

Example:
```sh
mdns-repeater eth0 vlan1
```

You can also specify the:
 - `-f` flag to keep `mdns-repeater` running in foreground.
 - `-d` flag additionally to `-f` to print out parsed `mDNS` packets as they are received

Docker image Usage
==================

Container is already configured for automatic restart (See `docker-compose.yml`).

* Configure environment:

  - `MDNS_REPEATER_INTERFACES`: names of the interfaces:

    ```sh
      export MDNS_REPEATER_INTERFACES="eth0 docker0"
    ```
  - `DOCKER_REGISTRY`: [**OPTIONAL**] registry prefix to pull image from a custom `Docker` registry:

    ```sh
      export DOCKER_REGISTRY="my_registry_hostname:5000/"
    ```
* Pull prebuilt `Docker` image:

  ```sh
    docker-compose pull
  ```
* Start prebuilt image:

  ```sh
    docker-compose up -d
  ```
* Stop/Restart:

  ```sh
    docker-compose stop
    docker-compose start
  ```

Acknowledgments
===============

- **Darell Tan** who created the initial version of this [program](https://github.com/geekman/mdns-repeater)
and who described it in this [blog post](http://irq5.io/2011/01/02/mdns-repeater-mdns-across-subnets/).
- **Kenny Levinsen** and contributors for maintaining the code and adding features in
this [repository](https://github.com/kennylevinsen/mdns-repeater).
- **Matthias Dettling** for `-d` flag idea in this [repository](https://github.com/devsecurity-io/mdns-repeater).
