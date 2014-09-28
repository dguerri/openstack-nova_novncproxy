Nova novncproxy
=========

OpenStack Nova novncproxy service installation

_Tested on Ubuntu Precise (12.04) and Trusty (14.04)_

Requirements
------------

A RabbitMQ server. See below.

Role Variables
--------------
### Nova novncproxy (set by this role)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `my_ip` | `{{ ansible_eth0.ipv4.address }}` | Management IP for nova-novncproxy ||
| `vncserver_proxyclient_address` | `{{ my_ip }}` | The address to use to connect to the vnc proxy ||
| `vncserver_proxy_address` | `{{ my_ip }}` | The address to which proxy clients should connect ||
| `novncproxy_base_url` | `"http://{{ vncserver_proxy_address }}:6080/vnc_auto.html"` | Desired novncproxy base_url ||


### RabbitMQ (must exist)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `rabbit_hostname` | `localhost` | Hostname/IP address where the RabbitMQ service runs ||
| `rabbit_username` | `rabbit_username_default` | RabbitMQ username for glance ||
| `rabbit_pass` | `rabbit_pass_default` | RabbitMQ password for glance. ||


Dependencies
------------

None.

Example Playbook
----------------

    - hosts: console001
      roles:
        - role: openstack-nova_novncproxy
          rabbit_username: "openstack-nova"
          rabbit_pass: "{{ RABBIT_NOVA_PASS }}"

---

A complete Ansible playbook demo, which uses this role, is available on Github (dguerri/vagrant-ansible-openstack) <https://github.com/dguerri/vagrant-ansible-openstack>

---

License
-------

Apache

Author Information
------------------

Davide Guerri - davide.guerri@gmail.com
