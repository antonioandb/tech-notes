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



