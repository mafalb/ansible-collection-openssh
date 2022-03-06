# Changelog

## v1.1.4 2022-XX-XX

- introduce variable container_build to support building containers without systemd
- remove support for centos 8

## v1.1.3 2021-12-18

- support for fedora 35
- support for ubuntu 21.10
- mask the service unit before installing (on debianish systems)
- bugfixes

## v1.1.2 2021-09-14

- fix sshd_config_template
- add option sshd_config_mode
- add support for ArchLinux
- CI on Debian 11 bullseye
- CI on Arch

## v1.1.0 2021-07-13

- add support for rocky

## v1.0.0 2021-05-28

### Changes

- configuration via yaml is possible

## v0.0.3 2021-02-06

### Changes

- Global block in sshd_config template
- work on CI
- fix an internal bug: do not use 'is true' tests (available only in newest jinja2)

## v0.0.2 2021-01-23

### Changes

- config value dict was not merged with default values
- sshd_config is validated

## v0.0.1 2021-01-23

### Changes

- initial release

