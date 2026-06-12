
# Instalação do VS Code no Debian/Ubuntu

## 1. Atualizar o sistema

```bash
sudo apt update
sudo apt upgrade -y
```

## 2. Instalar dependências

```bash
sudo apt install wget gpg apt-transport-https -y
```

## 3. Importar a chave da Microsoft

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | \
gpg --dearmor | \
sudo tee /usr/share/keyrings/microsoft.gpg > /dev/null
```

## 4. Adicionar o repositório oficial

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft.gpg] https://packages.microsoft.com/repos/code stable main" | \
sudo tee /etc/apt/sources.list.d/vscode.list
```

## 5. Atualizar a lista de pacotes

```bash
sudo apt update
```

## 6. Instalar o VS Code

```bash
sudo apt install code -y
```

## 7. Executar o VS Code

Pelo menu do sistema:

```text
Menu → Programação → Visual Studio Code
```

Ou pelo terminal:

```bash
code
```

---

# Verificar a instalação

```bash
code --version
```

Exemplo de saída:

```text
1.xx.x
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
x64
```

---

# Atualizações

Depois de instalado pelo repositório oficial, basta atualizar o sistema normalmente:

```bash
sudo apt update
sudo apt upgrade
```

O VSCode será atualizado junto com os demais pacotes.



