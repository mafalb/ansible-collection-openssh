# Ansible Role mafalb.openssh.sshd

Ansible role mafalb.openssh.sshd

## Basic Usage

```yaml
- name: install mafalb.openssh.sshd
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
```

you could write a custom template that extends sshd_config with a block "Matches", something like

```jinja2
{% extends "sshd_config.j2" %}
{% block Matches %}
{% if sftponly_group_matches is defined %}
{% for match in sftponly_group_matches %}
Match Group {{ match }}
        ChrootDirectory %h
        ForceCommand internal-sftp -f AUTH -l VERBOSE
        AllowTcpForwarding no
        X11Forwarding no
        PermitTTY no
{% endfor %}
{% endif %}
{% endblock %}
```

and then you would use it like

```yaml
- name: install mafalb.openssh.sshd
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
    sshd_config_template: test.conf.j2
    sftponly_group_matches:
    - "*,!root,!wheel"
```

```yaml
- name: remove sshd
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
    state: absent
```

## Variables

```state: present``` # [present|absent]

```sshd_config_template: test.conf.j2``` # [sshd_config.j2]

## License

GPLv3
