weave
=========

Set up a weave network handle by systemd services.

Requirements
------------

This module assumes docker is installed in the target machine.

Role Variables
--------------
```
---
# defaults file for weave
weave_server_group: weave_servers
weave_launch_peers: "{% for host in groups[weave_server_group] %}{% if host != inventory_hostname %}{{ hostvars[host].ansible_default_ipv4.address }} {% endif %}{% endfor %}"
weave_proxy_args: '--rewrite-inspect --without-dns'
weave_router_args: '--no-dns'
weave_version: 1.4.5
weave_url: "https://github.com/weaveworks/weave/releases/download/v{{ weave_version }}/weave"
weave_bin: /mnt/weave

# scope
scope_url: https://github.com/weaveworks/scope/releases/download/latest_release/scope
scope_bin: /mnt/scope
```

License
-------

MIT
