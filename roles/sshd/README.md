# Ansible Role mafalb.openssh.sshd

Ansible role mafalb.openssh.sshd

## Basic Usage

```yaml
- name: install mafalb.openssh.sshd
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
```

you could write a custom template that extends the base template from the role with a block named "Matches", something like

```jinja2
{% extends "mafalb.openssh.sshd_config.j2" %}
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

also note that if you do not extend the template you can specify a completely standalone config file/template

you can also remove openssh

```yaml
- name: remove sshd
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
    state: absent
```

## Variables

```state: present``` # [present|absent]

```sshd_config_template: test.conf.j2```

## License

GPLv3
