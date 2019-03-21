[![Build Status](https://travis-ci.org/open-io/ansible-role-openio-ROLENAME.svg?branch=master)](https://travis-ci.org/open-io/ansible-role-openio-ROLENAME)
# Ansible role `ROLENAME`

An Ansible role for PURPOSE. Specifically, the responsibilities of this role are to:

-

## Requirements

- Ansible 2.4+

## Role Variables

| Variable                               | Description                                 | Type    |
| -------------------------------------- | ------------------------------------------- | ------- |
| `openio_filebeat_gridinit_dir`         | Gridinit service directory                  | string  |
| `openio_filebeat_gridinit_file_prefix` | Gridinit file prefix                        | string  |
| `openio_filebeat_namespace`            | Filebeat namespace                          | string  |
| `openio_filebeat_pid_directory`        | Filebeat PID directory                      | string  |
| `openio_filebeat_provision_only`       | Provision only, without restarting services | boolean |
| `openio_filebeat_serviceid`            | Filebeat service id                         | integer |
| `openio_filebeat_volume`               | Filebeat internal directory                 | string  |
| `openio_filebeat_es_hosts`             | Elasticsearch cluster to send data to       | list    |


## Dependencies

No dependencies.

## Example Playbook

```yaml
- hosts: all
  become: true
  vars:
    NS: OPENIO

  roles:
    - role: repo
      openio_repository_products:
        sds:
          release: "18.10"
    - role: users
    - role: gridinit
      openio_gridinit_namespace: "{{ NS }}"
    - role: role_under_test
      openio_ROLENAME_namespace: "{{ NS }}"
```


```ini
[all]
node1 ansible_host=192.168.1.173
```

## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section.

Pull requests are also very welcome.
The best way to submit a PR is by first creating a fork of this Github project, then creating a topic branch for the suggested change and pushing that branch to your own fork.
Github can then easily create a PR based on that branch.

## License

GNU AFFERO GENERAL PUBLIC LICENSE, Version 3

## Contributors

- [Cedric DELGEHIER](https://github.com/cdelgehier) (maintainer)
- [Romain ACCIARI](https://github.com/racciari) (maintainer)
- [Vincent LEGOLL](https://github.com/vincent-legoll) (maintainer)
