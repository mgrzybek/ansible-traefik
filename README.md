ansible-traefik
===============

Deploy Traefik reverse-proxy.

Requirements
------------

You need to be able to download traefik binary or copy it yourself on the 
servers.

Role Variables
--------------

By default `traefik_package_state` is set to `present` and uses 
`traefik_version`. You can set `traefik_package_state` to `latest` and check 
the official website and dowanload the last version available.

In a high-available environment two variables are used:
* `traefik_cluster_aware` should be set to `true`
* `traefik_cluster_resource_name` should be given

Dependencies
------------

This playbook is standalone.

Example Playbook
----------------

Deploy a non-root running traefik service:

    - hosts: servers
      role: ansible-traefik

Deploy a traefik service as a container. Metrics are sent to an InfluxDB v1
endpoint:

    - hosts: servers
      role: ansible-traefik
      vars:
        # Packaging
        traefik_use_docker: true
        # Metrics
        traefik_metrics_influxdb_endpoint: http://metrics.example.com:8086
        traefik_metrics_influxdb_push_interval: 60s

License
-------

GPL-3+

Author Information
------------------

Mathieu GRZYBEK
