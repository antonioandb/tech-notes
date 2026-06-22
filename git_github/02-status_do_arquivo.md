# verificando o status do arquivo
o principal comando para verificar quais arquivos estão quais estados é:
```bash
git status
```
se o resultado for esse:
```bash
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
``` 
quer dizer que nenhum arquivo rastreado foi modificado, se existise algum arquivo não rastreado ou modificado apareceria aqui.

## rastreando novos arquivos
para começar a restrear um arquivo:
```bash
git add <arquivo>
```
isso leva o arquivo para a area de staged,todos os arquivos nesse estado entrarão no proximo commit.

## git status curto
existem flags que deixam a saida do git status mais simples como:
```bash 
git status -s
git status --short
```
## fazendo commit das alterações
o commit cria uma "foto" de todos os arquivos que estão no stage.
```bash
git commit -m "mensagem"
```
é possivel deixar uma mensagem com o -m

é posivel "pular a stage" ou seja não precisar do comando git add e já commitar todos os arquivos rastreados:
```bash
git commit -a -m "mensagem"
```
mas isso deve ser feito com cuidado pois arquivos indesejados podem serem comitados.

## removendo arquivos
existe o comando: 
``` bash
git rm <arquivo>
```
esse comando remove o arquivo do stage e apaga ele do diretorio.
se simples mente o arquivo for apagado manualmente ele vai aparecer como "arquivo fora do stage" ou “Changes not staged for commit” na saida do git status.

o comando: 
```bash
git rm --cached <arquivo>
``` 
retira o arquivo do stage mas mantem o arquivo no diretorio.

é possivel remover varios arquivos:
```bash
git rm \*~
```
isso remove todos os arquivos que terminem com ~ do diretorio.
## renomeando arquivos
no git existe o comando `mv` que significa move, e o renomear é tratado como um caso especial de mover, então para renomear um arquivo o comando é:
```bash 
mv arquivo.txt novo_nome.txt
```

