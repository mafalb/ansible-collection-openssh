# Ansible Role mafalb.openssh.authorized_keys

Ansible role mafalb.openssh.authorized_keys

## Basic Usage

```yaml
- name: install mafalb.openssh.authorized_keys
  hosts: localhost
  roles:
  - role: mafalb.openssh.authorized_keys
    user: mafalb
    path: /home/mafalb/.ssh/authorized_keys
```

```yaml
- name: install mafalb.openssh.authorized_keys
  hosts: localhost
  roles:
  - role: mafalb.openssh.authorized_keys
    user: root
    group: user1
    mode: 00640
    path: /home/user1/.ssh/authorized_keys
```

## Variables

## License

GPLv3

