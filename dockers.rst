Docker
======

Daemon configuration is:
/etc/docker/daemon.json

Force containers to use host DNS (Ubuntu)
-----------------------------------------
https://github.com/moby/moby/issues/23910

add a file /etc/NetworkManager/dnsmasq.d/docker-bridge.conf::

    listen-address=172.17.0.1

restart network manager::

    service network-manager restart

edit /etc/docker/daemon.json::

    {
      "dns": ["172.17.0.1"]
    }

restart docker daemon::
    service docker restart

Dockers behind proxy
--------------------

Start docker::

    docker build -t sbery-api --build-arg http_proxy=http://proxy.wdf.sap.corp:8080  --build-arg https_proxy=http://proxy.wdf.sap.corp:8080 .
