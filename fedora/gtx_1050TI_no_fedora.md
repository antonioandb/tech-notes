# Instalação do Driver NVIDIA GTX 1050 Ti no Fedora Cinnamon 44

## 1. Atualizar o sistema

```bash
sudo dnf upgrade --refresh
sudo reboot
```

---

## 2. Habilitar os repositórios RPM Fusion

```bash
sudo dnf install \
https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-44.noarch.rpm \
https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-44.noarch.rpm
```

Atualize os repositórios:

```bash
sudo dnf upgrade --refresh
```

---

## 3. Instalar o driver NVIDIA série 580

**Importante:** No meu caso a série 595 não funcionou com a GTX 1050 Ti. A série 580 funcionou corretamente.

Instalar:

```bash
sudo dnf install \
akmod-nvidia-580xx \
xorg-x11-drv-nvidia-580xx \
xorg-x11-drv-nvidia-580xx-cuda
```

Para jogos (Steam, Heroic, Lutris e Proton):

```bash
sudo dnf install \
xorg-x11-drv-nvidia-580xx-libs.i686
```

---

## 4. Compilar o módulo do kernel

Executar:

```bash
sudo akmods --force
```

Aguardar alguns minutos.

Verificar se o módulo foi criado:

```bash
modinfo nvidia
```

Deve aparecer algo parecido com:

```text
version: 580.159.04
```

---

## 5. Recriar a imagem de boot

```bash
sudo dracut --force
```

---

## 6. Reiniciar o computador

```bash
sudo reboot
```

---

## 7. Verificar se o driver carregou

```bash
lsmod | grep nvidia
```

Saída esperada:

```text
nvidia_drm
nvidia_modeset
nvidia_uvm
nvidia
```

---

## 8. Testar o NVIDIA-SMI

```bash
nvidia-smi
```

Saída esperada:

```text
NVIDIA GeForce GTX 1050 Ti
Driver Version: 580.159.04
```

---

## 9. Confirmar renderização OpenGL

Instalar ferramentas:

```bash
sudo dnf install mesa-demos
```

Verificar:

```bash
glxinfo | grep "OpenGL renderer"
```

Resultado esperado:

```text
OpenGL renderer string: NVIDIA GeForce GTX 1050 Ti/PCIe/SSE2
```

---

## Problema encontrado durante a instalação

O driver:

```text
595.80
```

foi instalado corretamente, compilou normalmente, porém apresentava o erro:

```text
NVRM: nvidia.ko because it does not include the required GPU
```

A GPU não era reconhecida.

A solução foi remover a série 595 e instalar a série:

```text
580.159.04
```

que funcionou normalmente.

---

## Verificação final

```bash
nvidia-smi
```

Deve mostrar:

- NVIDIA GeForce GTX 1050 Ti

- Driver 580.159.04

- Memória de vídeo disponível

- Processos Xorg e Cinnamon utilizando a GPU
