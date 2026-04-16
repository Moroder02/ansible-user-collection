# Ansible проект для сбора информации о пользователях и копирования ключа

## Структура проекта

- `ansible.cfg` — конфигурация ansible, указывает инвентори
- `inventories/hosts.yml` — список хостов
- `inventories/host_vars/<host>.yml` — отдельный логин и пароль для каждого сервера
- `playbooks/collect_users.yml` — сбор пользователей и групп
- `playbooks/deploy_ssh_key.yml` — копирование публичного ключа Ansible-сервера
- `files/ansible_id_rsa.pub` — публичный ключ, который будет копироваться на хосты

## Использование

1. Замените в `inventories/host_vars/<host>.yml` реальные логины и пароли.
2. Поместите публичный ключ Ansible-сервера в `files/ansible_id_rsa.pub`.
3. Запустите сбор информации:

```bash
ansible-playbook playbooks/collect_users.yml
```

4. Запустите копирование ключа на хосты:

```bash
ansible-playbook playbooks/deploy_ssh_key.yml
```

## Примечания

- Каждый хост использует свои отдельные `ansible_user` и `ansible_password`.
- `host_vars` обеспечивает хранение учетных данных отдельно от общего инвентаря.
