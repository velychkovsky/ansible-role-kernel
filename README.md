<!---
Документация по оформлению README.md описана в https://docs.ahback.com/x/YoXiAQ

Ссылки на иконки (прямая ссылка и сокращенный вариант):
https://nexus.ahback.com/repository/public/icons/ansible-shared-roles-versions/alpha.png - https://cutt.ly/5hbiBil
https://nexus.ahback.com/repository/public/icons/ansible-shared-roles-versions/beta.png - https://cutt.ly/OhbiLir
https://nexus.ahback.com/repository/public/icons/ansible-shared-roles-versions/stable.png - https://cutt.ly/7hbu2Ze
https://nexus.ahback.com/repository/public/icons/ansible-shared-roles-versions/deprecated.png - https://cutt.ly/jhbiKOG
https://nexus.ahback.com/repository/public/icons/ansible-shared-roles-platforms/centos7.png - https://cutt.ly/Khbu0xO
https://nexus.ahback.com/repository/public/icons/ansible-shared-roles-platforms/debian10.png - https://cutt.ly/ghbu8oA
https://nexus.ahback.com/repository/public/icons/ansible-shared-roles-platforms/ubuntu18.png - https://cutt.ly/8hbu6WF
https://nexus.ahback.com/repository/public/icons/ansible-shared-roles-platforms/ubuntu20.png - https://cutt.ly/0hbiTvl
--->

### Description

Роль предназначена для установки ядра системы.

### OS support

- <img src="https://cutt.ly/7hbu2Ze" width="24" height="24" title="In production"><img src="https://cutt.ly/Khbu0xO" width="24" height="24"> CentOS 7
- <img src="https://cutt.ly/OhbiLir" width="24" height="24" title="Tested in sandbox"><img src="https://cutt.ly/ghbu8oA" width="24" height="24"> Debian 10 Buster
- <img src="https://cutt.ly/7hbu2Ze" width="24" height="24" title="In production"><img src="https://cutt.ly/8hbu6WF" width="24" height="24"> Ubuntu 18.04 Bionic Beaver
- <img src="https://cutt.ly/7hbu2Ze" width="24" height="24" title="In production"><img src="https://cutt.ly/0hbiTvl" width="24" height="24"> Ubuntu 20.04 Focal Fossa

<!--- Раздел о том, как устанавливать роль --->

## Installation

Добавляем в `roles/requitements.yml`:

```yaml
- name: linux/kernel
  src: git+git@git.ahback.com:ansible-roles/linux/kernel.git
  version: master
```

Переходим в папку с проектом и запускаем установку роли:

```bash
ansible-galaxy install -r roles/requirements.yml
```

<!--- Раздел о том, как использовать роль --->

## Usage

```yaml
- name: Setup linux kernel
  hosts: all
  vars_prompt:
  - name: kernel_allow_reboot
    prompt: Allow to reboot kernel if it may changed?
    default: no
    private: no
  roles:
  - role: linux/kernel
```

<!--- Раздел о том, какие вещи можно кастомизировать, и что вообще к чему относится --->

## Documentation

### Variables

| Name								| Default Value					| Definition	| Description	|
| --------------------------------- | ----------------------------- | ------------- | ------------- |
| `kernel_allow_reboot`				| `false` (boolean)				| _optional_	| Флаг, которым мы разрешаем перезагрузку всего сервера, если во время деплоя пакетов, будут внесены изменения	|
| `linux_kernel_version`			| (object)						| _optional_	| 	|
| `linux_kernel_version.centos7`	| [See here](defaults/main.yml)	| _optional_	| Версия ядра для CentOS 7	|
| `linux_kernel_version.debian10`	| [See here](defaults/main.yml)	| _optional_	| Версия ядра для Debian 10	|
| `linux_kernel_version.ubuntu1804`	| [See here](defaults/main.yml)	| _optional_	| Версия ядра для Ubuntu 18.04	|
| `linux_kernel_version.ubuntu2004`	| [See here](defaults/main.yml)	| _optional_	| Версия ядра для Ubuntu 20.04	|

### Files

Отсутствуют

### Templates

Отсутствуют

### Systemd services

Отсутствуют

### Firewall settings

Отсутствуют

### Sysctl settings

Отсутствуют

<!--- Раздел с полезными ссылками, относящимися к роли --->

## References

- https://packages.debian.org/ru/sid/netfilter-persistent