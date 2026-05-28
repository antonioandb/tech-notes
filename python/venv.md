# Ambiente virtual Python (venv)
## O que é um ambiente virtual?

Um ambiente virtual é um ambiente isolado do Python usado para instalar bibliotecas e dependências sem afetar o sistema operacional ou outros projetos.

Cada projeto pode ter:

- sua própria versão do Python
- suas próprias bibliotecas
- versões diferentes das mesmas bibliotecas

Isso evita conflitos entre projetos.

## Por que usar ambiente virtual?

Sem ambiente virtual, os pacotes instalados com pip ficam disponíveis globalmente no sistema.

Isso pode causar problemas como:

- conflitos de versões
- quebra de projetos antigos
- dependências misturadas
- bagunça no sistema

Com o venv, cada projeto fica isolado.

## Meu fluxo de criação de ambiente isolado

Primeiro, criar ou entrar na pasta do projeto:
```bash
mkdir projeto
cd projeto
```
Já dentro da pasta especificar a versão do python que o projeto vai usar:
```bash
pyenv local 3.13.13
```
Criar o ambiente virtual.
```bash
python -m venv .venv
```
Isso cria uma pasta chamada .venv contendo o ambiente virtual.

## Ativando o ambiente virtual
```bash
source .venv/bin/activate
```
Após ativar, normalmente o terminal mostra algo assim:
```bash
(.venv)
```
Verificando o python ativo:
```bash
which python
```
Resultado esperado:
```bash
/home/user/projeto/.venv/bin/python
```
Isso confirma que o ambiente virtual está sendo usado.

Desativando o ambiente:
```bash
deactivate
```

## Observações

Em distribuições Debian/Ubuntu modernas, o comando `python`
pode não existir por padrão.

Nesses casos use:

```bash
python3
```
