## Deprecated

This package will no longer be updated. In it's current state it won't work for Debian Buster.

Memcached
========

Install and start memcached

#### Version 2.0: Add multi-instance configuration support

BC break: the default Listen directive is now "127.0.0.1"

Requirements
------------

Debian Bullseye / Bookworm with the package python-pycurl and python-software-properties installed.

Role Variables
--------------

### Single instance installation:

    # Listen on IP
    memcached_listen: 127.0.0.1  
    memcached_port: 11211

    # Or: Listen on a socket
    memcached_socket: /var/run/memcached/memcached.sock
    memcached_permissions: "0666"
    
    memcached_maxconn: 1024
    memcached_memusage: 128

### When using multiple instances 
(single instance variables will be ignored):

    memcached_servers:
      - name: production
        maxconn: 1024
        memusage: 128
        listen: 127.0.0.1
        port: 11211
      - name: development
        maxconn: 1024
        memusage: 128
        socket: "/var/run/memcached/memcached_development.sock"
        permissions: "0666"

Example Playbook
-------------------------

    - hosts: servers
      roles:
         - { role: f500.memcached }

License
-------

LGPL

Author Information
------------------

Jasper N. Brouwer, jasper@nerdsweide.nl

Ramon de la Fuente, ramon@delafuente.nl
