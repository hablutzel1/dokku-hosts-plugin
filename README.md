Hosts Plugin for Dokku
======================

Plugin for setting `etc/hosts` entries within the app container

Project: https://github.com/dokku/dokku

**Warning: This plugin is under development and still only tested with the below dependencies**


Useful when needing to set a host to be accessed within one app and for some reason using the IP address is not an option.

For example, when you have another dokku instance running at `199.10.32.3` and you access it via `myapp.dokku.me` mapped in your dev machine's `/etc/hosts` file:

```
# /etc/hosts
199.10.32.3 myapp.dokku.me
```

Requirements
------------

Last time tested with the following:

* Docker version `18.06.1-ce`
* Dokku version `0.12.13`

Installation
------------
```
cd /var/lib/dokku/plugins/available
git clone https://github.com/hablutzel1/dokku-hosts-plugin/ hosts
dokku plugin:enable hosts
```

Commands
--------
```
$ dokku help
    hosts:add <app> <ip> <hostname>                 Sets <ip> and <hostname> for <app>
    hosts:list <app>                                Lists all custom hosts set for <app>
    hosts:remove <app> <hostname>                   Removes <hostname> from <app>
    hosts:removeall <app>                           Removes all hosts set for <app>
```

Simple usage
------------

Make sure your app is running.

Add a ip/hostname to your app's `etc/hosts`

```bash
$ dokku hosts:add myapp 0.0.0.0 myhost.com 
```

List currently set hosts

```bash
$ dokku hosts:list myapp
```

Advanced usage
--------------

Remove one entry

```bash
$ dokku hosts:remove myapp myhost.com
```

Remove all entries

```bash
$ dokku hosts:removeall myapp
```

TODO
----

* Set configured hosts to every created app container, not just the ones existing after a deploy [#1](/../../issues/1)
