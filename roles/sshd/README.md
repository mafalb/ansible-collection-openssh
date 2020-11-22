# Ansible Role mafalb.openssh.sshd

Ansible role mafalb.openssh.sshd

## Basic Usage

```yaml
- name: install mafalb.openssh.sshd
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
```

```yaml
- name: remove sshd
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
    sshd_state: absent
```

## Variables

```ssh_state: present``` # [present|absent]

## License

GPLv3
