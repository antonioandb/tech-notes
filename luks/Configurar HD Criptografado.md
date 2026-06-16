# Configurar HD Criptografado (LUKS) para Montagem Automática no Fedora

## 1. Identificar o disco

```bash
lsblk -f
```

Exemplo:

```text
sdb1 crypto_LUKS UUID=faff00a3-5000-4029-b759-080b78557ffe
```

---

## 2. Desbloquear manualmente

```bash
sudo cryptsetup open /dev/sdb1 dados
```

Verificar o sistema de arquivos interno:

```bash
lsblk -f
```

Exemplo:

```text
sdb1
└─dados ext4 UUID=bb65fca2-9c05-4c3f-bf6f-00f367908635
```

---

## 3. Criar o ponto de montagem

```bash
sudo mkdir -p /mnt/dados
```

---

## 4. Criar um arquivo de chave

```bash
sudo mkdir -p /root/keys

sudo dd if=/dev/urandom of=/root/keys/dados.key bs=4096 count=1

sudo chmod 600 /root/keys/dados.key
```

---

## 5. Adicionar a chave ao LUKS

```bash
sudo cryptsetup luksAddKey /dev/sdb1 /root/keys/dados.key
```

Será solicitada a senha atual do HD.

---

## 6. Configurar o crypttab

Editar:

```bash
sudo nano /etc/crypttab
```

Adicionar:

```text
dados UUID=faff00a3-5000-4029-b759-080b78557ffe /root/keys/dados.key luks
```

Manter a entrada original do sistema.

Exemplo:

```text
luks-f0b31c02-f93f-453e-8b29-15880980ac53 UUID=f0b31c02-f93f-453e-8b29-15880980ac53 none discard,x-initrd.attach
dados UUID=faff00a3-5000-4029-b759-080b78557ffe /root/keys/dados.key luks
```

---

## 7. Configurar o fstab

Editar:

```bash
sudo nano /etc/fstab
```

Adicionar:

```text
UUID=bb65fca2-9c05-4c3f-bf6f-00f367908635 /mnt/dados ext4 defaults,nofail 0 2
```

---

## 8. Recriar o initramfs

```bash
sudo dracut --force
```

---

## 9. Recarregar configurações

```bash
sudo systemctl daemon-reload
```

---

## 10. Reiniciar

```bash
sudo reboot
```

---

## Verificação

Confirmar que o volume foi aberto:

```bash
lsblk -f
```

Resultado esperado:

```text
sdb1
└─dados ext4 Dados ...
              /mnt/dados
```

Verificar a montagem:

```bash
mount | grep /mnt/dados
```

ou

```bash
df -h | grep dados
```

---

## Observações

- O HD será desbloqueado automaticamente durante o boot.

- Não será necessário digitar a senha do HD.

- A chave fica armazenada em:

```text
/root/keys/dados.key
```

- Se o HD for removido, o sistema continuará iniciando normalmente por causa da opção `nofail` no `/etc/fstab`.
