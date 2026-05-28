# instalação do pyenv em distros base debian/ubuntu


## 1 instalação de dependencias 

```bash
sudo apt update

sudo apt install -y \
  build-essential curl git \
  libssl-dev zlib1g-dev \
  libbz2-dev libreadline-dev \
  libsqlite3-dev wget llvm \
  libncursesw5-dev xz-utils tk-dev \
  libxml2-dev libxmlsec1-dev \
  libffi-dev liblzma-dev ca-certificates
```

Esses pacotes são importantes porque o pyenv compila versões do Python do zero.



## 2 instalando o pyenv 

```bash
curl https://pyenv.run | bash
```

usando o instalador oficial: [GitHub - pyenv/pyenv: Simple Python version management · GitHub](https://github.com/pyenv/pyenv?utm_source=chatgpt.com)



## 3 configurando o bash ↓

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc
```

depois recarregue o bash:

```bash
source ~/.bashrc
```

caso tiver usando zsh:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init - zsh)"' >> ~/.zshrc

source ~/.zshrc
```


## 4 veficação 

verifica se funcionou:

```bash
pyenv --version
```

isso mostra a versão do pyenv



## 5 instalar uma versão do python

listar versão disponiveis:

```bash
pyenv install --list
```

instalar uma versão especifica, por exemplo:

```bash
pyenv install 3.13.13
```


### definindo uma versão padrão

global(sistema do usuario inteiro):

```bash
pyenv global 3.12.3
```
ou

local(espeficar vesão para cada projeto):

```bash
pyenv local 3.12.3
```

eu gosto de manter o python que já veio com o sistema como padrão e só usar uma versão especifiaca do python na hora de criar o ambiente isolado do projeto, emtão para garantir que o python global seja o do sistema eu uso o comando:

```bash
pyenv global system
```

verifica as versões do python instaladas:

```bash
pyenv versions
```

isso mostra uma lista de versões do python instaladas e qual é a versão padrão.

## outros comandos uteis
### Verificar qual Python está sendo usado

```bash
which python
```

Esse comando mostra qual executável do Python está sendo utilizado no momento.

### Listar versões instaladas:
```bash
pyenv versions
```
### Atualizar pyenv:
```bash
cd ~/.pyenv
git pull
```

### Remover uma versão:
```bash
pyenv uninstall 3.11.9
```
