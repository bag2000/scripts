```bash
EDITOR=nano ansible-vault create vars/secret.yml
ansible-playbook -i inventories/hosts playbooks/setup_ipa_client.yml -u ans --private-key ~/.ssh/id_ed25519_sk_yubikey --ask-vault-pass
```