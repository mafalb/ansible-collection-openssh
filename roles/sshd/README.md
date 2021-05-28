# Ansible Role mafalb.openssh.sshd

Ansible role mafalb.openssh.sshd

## Basic Usage

```yaml
- name: default settings
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
```

```yaml
- name: pass a custom template
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
    sshd_config_template: /path/to/template.j2
```

or you can use the default template and pass sshd configuration as yaml

```yaml
- name: configuration as yaml
  hosts: localhost
  roles:
  - role: mafalb.openssh.sshd
    sshd_config:
      PermitRootLogin: without-password
      PasswordAuthentication: 'no'
      Match:
        'Group sftpchroot':
          ChrootDirectory: '%h'
          AuthorizedKeysFile: /etc/ssh/authorized_keys/sftpchroot .ssh/authorized_keys
          ForceCommand: internal-sftp
```

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
