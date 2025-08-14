### Настройка пользователя с правами sudo через Ansible
Данная роль автоматизирует установку и настройку sudo, создание пользователя, добавление SSH-ключа и настройку прав в sudoers

### Запуск
```bash
git clone https://github.com/bag2000/scripts.git
cd scripts/ansible
mkdir roles/ansible_user/files
cat YOUR-PUB-KEY > roles/ansible_user/files/authorized_keys
ansible-playbook -i inventories/hosts playbooks/setup_ansible_user.yml -u root
```

### Что делает
Установка пакета sudo на системах Debian/Ubuntu и RHEL/CentOS. <br>
Перезагрузка сервера после установки sudo (если требовалось).
Создание группы и пользователя с заданными параметрами.
Настройка домашней директории и shell пользователя.
Создание директории ~/.ssh и установка корректных прав.
Копирование публичного SSH-ключа.
Настройка правил в sudoers.

### Переменные
Роль использует следующие переменные (заданы в defaults/main.yml):

| Переменная             | Описание                         | Пример                                             |
| ---------------------- | -------------------------------- | -------------------------------------------------- |
| `ansible_user_name`    | Имя создаваемого пользователя    | `ans`                                              |
| `ansible_user_groups`  | Группа пользователя              | `sudo`                                             |
| `ansible_user_shell`   | Путь к shell                     | `/bin/bash`                                        |
| `ansible_user_home`    | Домашняя директория пользователя | `/home/{{ ansible_user_name }}`                    |
| `ansible_user_ssh_key` | Путь для `authorized_keys`       | `{{ ansible_user_home }}/.ssh/authorized_keys`     |
| `ansible_user_sudoers` | Правила sudo                     | `{{ ansible_user_name }} ALL=(ALL) NOPASSWD: ALL`  |

### Структура файлов
```bash
defaults/main.yml       # Переменные
tasks/main.yml          # Основной плейбук
files/authorized_keys   # Публичный ключ для пользователя
templates/sudoers.j2    # Шаблон sudoers
```