| Переменная             | Описание                         | Пример                                             |
| ---------------------- | -------------------------------- | -------------------------------------------------- |
| `ansible_user_name`    | Имя создаваемого пользователя    | `ans`                                              |
| `ansible_user_groups`  | Группа пользователя              | `sudo`                                             |
| `ansible_user_shell`   | Путь к shell                     | `/bin/bash`                                        |
| `ansible_user_home`    | Домашняя директория пользователя | `/home/{{ ansible_user_name }}`                    |
| `ansible_user_ssh_key` | Путь для `authorized_keys`       | `{{ ansible_user_home }}/.ssh/authorized_keys`     |
| `ansible_user_sudoers` | Правила sudo                     | `{{ ansible_user_name }} ALL=(ALL) NOPASSWD: ALL`  |