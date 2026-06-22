# Configurações iniciais do git no linux
## Configurar usuário
```bash
git config --global user.name "Nome"
git config --global user.email "exemplo@gmail.com"
```

## Verificar configuração
```bash
git config --list
```

## Gerar chave SSH
```bash
ssh-keygen -t ed25519 -C "exemplo@gmail.com"
```

## Exibir chave pública
```bash
cat ~/.ssh/id_ed25519.pub
```

## Adicionar a chave ao GitHub
**https://github.com/settings/keys**

## Testar conexão
```bash
ssh -T git@github.com
```

## iniciando um repositorio
para iniciar um repositorio local o comando é: 
```bash
git init
```
isso cria um subdiretório nomeado .git que contém todos os arquivos necessarios, depois disso é só começar a rastrear os arquivos e fazer os primeiros commits.

## Clonagem de um repositório existente
para obter uma copia completa de um repositorio o comando é:
```bash
git clone <url>
```
isso já cria o diretorio do projeto e inicializa o .git dentro dele.

também é possivel clonar um repositorio é escolher o nome da pasta:
```bash
git clone <url> nome
```
isso faz a mesma coisa que o anterior mas tambem cria a pasta local com o nome que foi escolhido.



