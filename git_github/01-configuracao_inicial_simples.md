# Configurar usuário
```bash
git config --global user.name "Nome"
git config --global user.email "exemplo@gmail.com"
```

# Verificar configuração
```bash
git config --list
```

# Gerar chave SSH
```bash
ssh-keygen -t ed25519 -C "exemplo@gmail.com"
```

# Exibir chave pública
```bash
cat ~/.ssh/id_ex25519.pub
```

# Adicionar a chave ao GitHub
**https://github.com/settings/keys**

# Testar conexão
```bash
ssh -T git@github.com
```