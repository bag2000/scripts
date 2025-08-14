# Для работы с Yubikey 5 FIDO с касанием
```bash
# Генерируем ключ
ssh-keygen -t ed25519-sk -O resident -f ~/.ssh/id_ed25519_sk_yubikey

# Копируем ключ на сервер
ssh-copy-id -i ~/.ssh/id_ed25519_sk_yubikey.pub ans@test

# Добавляем в ~/.ssh/config
Host test
  HostName your_server_ip
  User ans
  IdentityFile ~/.ssh/id_ed25519_sk_yubikey
  ControlMaster auto
  ControlPath ~/.ssh/ansible-%r@%h:%p
  ControlPersist 5m
  IdentitiesOnly yes
```

