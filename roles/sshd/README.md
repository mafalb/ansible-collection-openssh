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
{% if sftponly_group is defined %}
Match Group {{ sftponly_group }}
        ChrootDirectory %h
        ForceCommand internal-sftp -f AUTH -l VERBOSE
        AllowTcpForwarding no
        X11Forwarding no
        PermitTTY no
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
    sftponly_group: whatevergroup
```

also note that if you do not extend the template you can specify a completely standalone config file/template

you can also remove openssh if you want.

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
