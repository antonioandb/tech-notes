# montando meu ambiente de estudos no fedora

## vscode

Importar a chave da Microsoft: 

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```

Adicionar o repositório:

```bash
sudo sh -c 'echo -e "[code]
name=Visual Studio Code
baseurl=https://packages.microsoft.com/yumrepos/vscode
enabled=1
gpgcheck=1
gpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
```

Atualizar repositorios:

```bash
sudo dnf check-update
```

Instalar o vc code:

```bash
sudo dnf install code
```

Pronto

## Pyenv no Fedora

instalar dependencias:

```bash
sudo dnf install -y \
gcc make patch zlib-devel bzip2 bzip2-devel \
readline-devel sqlite sqlite-devel openssl-devel \
tk-devel libffi-devel xz-devel ncurses-devel \
gdbm-devel libuuid-devel
```

instalar pyenv:

```bash
curl https://pyenv.run | bash
```

Configurar o shell:

em .bashrc adicionar

```bash
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"

eval "$(pyenv init - bash)"
```

depois de salvar recarregar:

```bash
source ~/.bashrc
```

verificar instalação:

```bash
pyenv --version
```

Comandos:

- pyenv install --list : lista versões do python disponiveis

- pyenv install 3.13.7 :  instala uma versão especifica

- pyenv versions : ver versões instaladas

- pyenv global 3.13.7 : definir global

eu gosto de usar localmente para cada projeto

dentro da pasta do projeto:

```bash
pyenv local 3.13.7
```

isso cria um arquivo chamado .python-version que contem a versão que aquele projeto vai usar



## criando um ambiente virtual

dentro da pasta do projeto:

```bash
python -m venv .venv
```

- python = executa o interpretador python

- -m = executa um módulo Python.

- venv = é o módulo responsável por criar ambientes virtuais.

- .venv = nome da pasta onde o ambiente é criado

- 

estrutura criada:

```
.venv/
├── bin/
│   ├── python
│   ├── pip
│   └── activate
├── include/
├── lib/
└── pyvenv.cfg
```

ativando o ambiente:

```bash
source .venv/bin/activate
```

o teminal ficara com o prefixo (.venv) indicando que o ambinete está ativo para desativar o ambiente e só executar o comando: `deactivate`


