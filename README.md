Qafoo Consul
============

Ansible Consul role which is foundational to the whole stack.

Distributes service names and configuration (12factor).

Requirements
------------

- Ubuntu Server
- Servers with this role must have the Ansible groups `consul`, up to five of them `consul_server`

Role Variables
--------------

Example Playook
---------------

Minimal example:

    ---
    - hosts: all
      roles:
        - role: "qafoo.consul"

All hosts in ``consul_server`` group will be designated as consul servers, the
rest will be clients. All clients auto join the set of servers. Bootstrapping
is done automatically using ``consul_bootstrap_expect`` with the number of
server nodes.

Advanced example:

    ---
    - hosts: all
      roles:
        - role: "qafoo.consul"
          consul_node_name: "foo1"
          consul_datacenter: "dc1"
          consul_is_server: true
          # either
          consul_bootstrap: true
          # or
          consul_bootstrap_expect: 4

License
-------

Apache License

Parts are derived from the [jivesoftware/ansible-consul](https://github.com/jivesoftware/ansible-consul) role under Apache license as well.
