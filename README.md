dokku-nsinit
============

Execute commmands in the Docker containers.

> With great power comes great responsibility.

![](http://media.tumblr.com/b1370b7b7f035e8b62ae8d33e4fd0d4e/tumblr_inline_n9ee84uBgz1raprkq.gif)

Installation
------------

Clone:

```
$ cd /var/lib/dokku/plugins
$ git clone https://github.com/ryotarai/dokku-nsinit.git nsinit
```

Build nsinit:

```
# Make sure that go is installed.
$ go get github.com/docker/libcontainer/nsinit
$ cp $(which nsinit) /var/lib/dokku/plugins/nsinit/nsinit
```

Edit sudoer:

```
$ visudo
# Add the following line:
%dokku ALL=(ALL)NOPASSWD:/var/lib/dokku/plugins/nsinit/exec_nsinit
```

Usage
-----

```
$ ssh dokku@dokku-host nsinit app-name uptime
 14:35:01 up 1 days,  3:46,  0 users,  load average: 0.04, 0.03, 0.05
 Connection to dokku-host closed.
$ ssh -t dokku@dokku-host nsinit app-name /bin/bash
root@xxxxxxxxxxx:/# ls
app  boot   cache  etc   home  lib64  mnt  proc  run   selinux  start  tmp  var
bin  build  dev    exec  lib   media  opt  root  sbin  srv  sys    usr
```

