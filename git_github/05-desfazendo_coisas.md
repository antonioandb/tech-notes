# desfazendo coisas
o comando `git commit --amend` substitui o último commit por um novo commit.

exemplo:
```bash
git add arquivo.txt
git commit -m "Adiciona funcionalidade X"
```
percebeu que esqueceu de um arquivo
```bash
git add outro_arquivo.txt
git commit --amend
```
Se  salvar sem mudar nada, ele cria um novo commit contendo:

- arquivo.txt
- outro_arquivo.txt

## para alterar apenas a mensagem do commit
```bash
git commit --amend -m "Mensagem corrigida"
```
isso troca apenas a mensagem do ultimo commit.

é interessante fazer isso antes do `push` porque se não os arquivos locais vão ficar diferentes do arquivos do servidor.

## retirando um arquivo do stage

por exemplo se dois arquivos forem adicionados no stage mas o commit deles devem ser feito separadamente, é precisao tirar um deles.
```bash
git reset HEAD <file>...
```
o arquivo volta para o estado de modificado mas fica fora do stage.

## desfazendo alterações em um arquivo

o comando:
```bash
git checkout -- <arquivo>
```
o git descarta todas as alterações não commitadas do arquivo, deixando exatamente como no ultimo commit.

