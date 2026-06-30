### Create Vault Password

mkdir -p ~/.ansible
openssl rand -base64 32 > ~/.ansible/mt6000_vault_pass
chmod 600 ~/.ansible/mt6000_vault_pass


### Create secrets using VI

mkdir -p group_vars/router
ansible-vault create group_vars/router/vault.yaml \
  --vault-password-file ~/.ansible/mt6000_vault_pass


## Paste this in

---
route53_access_key_id: "YOUR_AWS_ACCESS_KEY_ID"
route53_secret_access_key: "YOUR_AWS_SECRET_ACCESS_KEY"