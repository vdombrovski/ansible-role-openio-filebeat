Ansible Role OpenIO Filebeat
=========

Installs Elastic's Filebeat for forwarding OpenIO logs.

Role Variables
--------------

 - `filebeat_version` - The version of filebeat to install. Defaults to `5.4.1`.
 - `filebeat_config` - YAML representation of our filebeat OpenIO specific configuration.

```yaml
filebeat_config:
  filebeat:
    prospectors:
      - paths:
          - /var/log/oio/sds/*/account*/*.log
          - /var/log/oio/sds/*/oio-event-agent*/*.log
          - /var/log/oio/sds/*/oioproxy*/*.log
          - /var/log/oio/sds/*/conscience*/*.log
          - /var/log/oio/sds/*/meta*/*.log
          - /var/log/oio/sds/*/account*/*.log.1
          - /var/log/oio/sds/*/oio-event-agent*/*.log.1
          - /var/log/oio/sds/*/oioproxy*/*.log.1
          - /var/log/oio/sds/*/conscience*/*.log.1
          - /var/log/oio/sds/*/meta*/*.log.1
        input_type: log
        document_type: logs
        scan_frequency: 5s
        close_removed: true
        close_inactive: 1m
        close_renamed: true
        ignore_older: 15m

      - paths:
          - /var/log/oio/sds/*/account*/*.access
          - /var/log/oio/sds/*/oio-event-agent*/*.access
          - /var/log/oio/sds/*/oioproxy*/*.access
          - /var/log/oio/sds/*/conscience*/*.access
          - /var/log/oio/sds/*/meta*/*.access
          - /var/log/oio/sds/*/account*/*.access.1
          - /var/log/oio/sds/*/oio-event-agent*/*.access.1
          - /var/log/oio/sds/*/oioproxy*/*.access.1
          - /var/log/oio/sds/*/conscience*/*.access.1
          - /var/log/oio/sds/*/meta*/*.access.1
        input_type: log
        document_type: access
        scan_frequency: 5s
        close_removed: true
        close_inactive: 1m
        close_renamed: true
        ignore_older: 15m

      - paths:
          - /var/log/oio/sds/*/rawx*/*httpd-errors.log
        input_type: log
        document_type: rawx-errors
        scan_frequency: 5s
        close_removed: true
        close_inactive: 1m
        close_renamed: true

      - paths:
          - /var/log/oio/sds/*/rawx*/*httpd-access.log
        input_type: log
        document_type: rawx-access
        scan_frequency: 5s
        close_removed: true
        close_inactive: 1m
        close_renamed: true


  output:
    logstash:
      hosts:
        - "{{ logstash_host }}"
  tls:
      certificate_authorities:
        - "{{ filebeat_ca_path }}"
  logging:
    to_files: true
    level: warning
    files:
      path: /var/log/mybeat
      name: mybeat.log
      keepfiles: 7
      rotateeverybytes: 10485760
  ```
  
 - `filebeat_ca_cert`, `filebeat_ca_path`  and `logstash_host`  are provided by ansible playbook.

Playbook example:
---------
```yaml
---
- name: Install and configure filebeat
  hosts: servers
  roles:
    - { role: ansible-filebeat-master, filebeat_ca_cert: "{{ lookup('file', '/etc/pki/tls/certs/logstash-forwarder.crt') }}",  filebeat_ca_path: /etc/pki/tls/certs/logstash-forwarder.crt, logstash_host: '172.16.139.250:5044' }
```


License
-------

BSD

Author Information
------------------

David Wittman
