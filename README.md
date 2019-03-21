[![Build Status](https://travis-ci.org/open-io/ansible-role-openio-filebeat.svg?branch=master)](https://travis-ci.org/open-io/ansible-role-openio-filebeat)
# Ansible role `filebeat`

An Ansible role for installing and configuring filebeat.

## Requirements

- Ansible 2.4+

## Role Variables

| Variable                               | Description                                   | Type    |
| -------------------------------------- | --------------------------------------------- | ------- |
| `openio_filebeat_version`              | Filebeat version to install                   | string  |
| `openio_filebeat_namespace`            | OpenIO Namespace to monitor                   | string  |
| `openio_filebeat_gridinit_dir`         | Filebeat gridinit directory                   | string  |
| `openio_filebeat_gridinit_file_prefix` | Gridinit unit prefix                          | string  |
| `openio_filebeat_pid_directory`        | Provision only, without restarting services   | boolean |
| `openio_filebeat_serviceid`            | Filebeat service id                           | integer |
| `openio_filebeat_volume`               | Filebeat internal directory                   | string  |
| `openio_filebeat_openio_log_path`      | Path to monitored openio log files            | string  |
| `openio_filebeat_es_hosts`             | List of Elasticseach IP:PORTs to send data to | list    |
| `openio_filebeat_provision_only`       | Provision only, without restarting            | boolean |
| `openio_filebeat_input_options`        | Filebeat options for processing logs          | dict    |
| `openio_filebeat_custom_inputs`        | Additional configs of log files to monitor    | list    |


## Dependencies

No dependencies.

## Example Playbook

[Example playbook](docker-tests/test.yml)

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
- [Vladimir DOMBROVSKI](https://github.com/vdombrovski) (maintainer)
