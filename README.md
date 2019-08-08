# Ansible role for HashiCorp Consul-template
=========

[![License](https://img.shields.io/badge/license-Apache-green.svg?style=flat)](https://raw.githubusercontent.com/lean-delivery/ansible-role-consul-template/master/LICENSE)
[![Build Status](https://travis-ci.org/lean-delivery/ansible-role-consul-template.svg?branch=master)](https://travis-ci.org/lean-delivery/ansible-role-consul-template)
[![Build Status](https://gitlab.com/lean-delivery/ansible-role-consul-template/badges/master/pipeline.svg)](https://gitlab.com/lean-delivery/ansible-role-consul-template/pipelines)
[![Galaxy](https://img.shields.io/badge/galaxy-lean__delivery.consul__template-blue.svg)](https://galaxy.ansible.com/lean_delivery/consul-template)
![Ansible](https://img.shields.io/ansible/role/d/42599.svg)
![Ansible](https://img.shields.io/badge/dynamic/json.svg?label=min_ansible_version&url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Froles%2F42599%2F&query=$.min_ansible_version)

Role for HashiCorp consul-template configuration

Requirements
------------

 - Minimal Version of the ansible for installation: 2.7
 - **Supported OS**:
   - CentOS
     - 7
   - RHEL
     - 7
   - Amazon Linux 2
   - Ubuntu
     - 18.04
   - Debian
     - 9

Role Variables
--------------

  - `bin_dir` - path to consul binaries.   
    Default is `/usr/local/bin`.
  - `start_script_path` - path to service scripts.   
    Default is `/etc/systemd/system`.
  - `consul_template_version` - version of consul-template.   
    Default: `0.20.0`.
  - `consul_template_config_path` - path to consul template config files.   
    Default is `/etc/consul-template`.
  - `consul_template_zip` - consul template archive name.   
    Default is `consul-template_{{ consul_template_version }}_linux_amd64.zip`.
  - `consul_template_url` - url path to download consul template.   
    Default is `https://releases.hashicorp.com/consul-template/{{ consul_template_version }}/{{ consul_template_zip }}`.
  - `consul_template_user` - user account to run consul service.   
    Default: `consul`.
  - `consul_quota_dir` - directory to store quota file.   
    Default: `/home/ggr/go-grid-router/quota`.
  - `consul_bin_file` - consul binary file path.   
    Default: `{{ bin_dir }}/consul-template`.
  - `consul_template_config` - consul tempate config name.   
    Default: `config-consul-template.conf`.
  - `consul_tpl_config` - grid router config template.   
    Default: `ggr-config-consul-template.tpl`.
  - `consul_xml_config` - grid router users xml config.   
    Default: `ggr-users.xml`.
  - `consul_template_additional_groups` - consul template additional groups list.   
    Default: `[]`.


Dependencies
------------

 - ansible role brianshumate.consul  [![Galaxy](https://img.shields.io/badge/galaxy-brianshumate.consul-blue.svg)](https://galaxy.ansible.com/brianshumate/consul)

Example Playbook
----------------

### Installing consul-template:
```yaml
- name: Install consul instances
  hosts: consul_instances
  become: true
  become_user: root
  roles:
    - role: brianshumate.consul
      consul_group_name: consul_instances
    - role: ansible-role-consul-template
  vars:
    consul_raw_key: ''
```

License
-------
Apache   
[![License](https://img.shields.io/badge/license-Apache-green.svg?style=flat)](https://raw.githubusercontent.com/lean-delivery/ansible-role-consul-template/master/LICENSE)

Author Information
------------------

authors:
  - Lean Delivery Team <team@lean-delivery.com>
