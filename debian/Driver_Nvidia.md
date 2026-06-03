# instalação do driver da nvidia no debian 13

## 1. Instale o Debian normalmente

Durante a instalação:

- Marque os repositórios:
  
  - `main`
  
  - `contrib`
  
  - `non-free`
  
  - `non-free-firmware`

Se não aparecer essa opção, você pode configurar depois.

---

## 2. Verifique o sources.list

No Debian 13 (Trixie), algo parecido com isto:

```bash
sudo nano /etc/apt/sources.list
```

```text
deb http://deb.debian.org/debian trixie main contrib non-free non-free-firmware
deb http://deb.debian.org/debian-security trixie-security main contrib non-free non-free-firmware
deb http://deb.debian.org/debian trixie-updates main contrib non-free non-free-firmware
```

Atualize:

```bash
sudo apt update
```

---

## 3. Atualize o sistema inteiro

Antes de instalar a NVIDIA:

```bash
sudo apt full-upgrade
sudo reboot
```

Isso evita instalar o driver em cima de um sistema parcialmente atualizado.

---

## 4. Instale os pacotes essenciais

```bash
sudo apt install build-essential dkms
```

Eles serão usados para recompilar o módulo NVIDIA quando o kernel mudar.

---

## 5. Instale os meta-pacotes do kernel

**Este é o um passo importante.**

```bash
sudo apt install linux-image-amd64 linux-headers-amd64
```

Os meta-pacotes garantem que futuras atualizações tragam automaticamente o novo kernel e os novos headers.

---

## 6. Instale o driver NVIDIA

```bash
sudo apt install nvidia-driver
```

O Debian puxará as dependências necessárias, incluindo DKMS.

---

## 7. Reinicie

```bash
sudo reboot
```

---

## 8. Verifique se tudo carregou

```bash
nvidia-smi
```

```bash
lsmod | grep nvidia
```

```bash
glxinfo | grep renderer
```

Se não tiver o `glxinfo`:

```bash
sudo apt install mesa-utils
```

---

## 9. Verifique o DKMS

Comando:

```bash
dkms status
```

Você deve ver algo parecido com:

```text
nvidia/xxx.xx, 6.x.x-amd64, x86_64: installed
```

---

## 10. Após cada atualização de kernel

Antes de reiniciar:

```bash
dkms status
```

Se aparecer o módulo NVIDIA compilado para o novo kernel, está tudo certo.

 também dá para conferir:

```bash
dpkg -l | grep linux-headers
```

e verificar se os headers da nova versão foram instalados.