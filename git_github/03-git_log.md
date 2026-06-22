# O comando git log
O comando git log é usado para visualizar o histórico de commits de um repositório, ultil para investigar alterações e entender a evolução do projeto.
Comando basico:
```bash
git log
```
vai exibir uma lista de commits do mais recente para o mais antigo.

exemplo:
```
commit 4d7f8a2c5e8f9b1e6d3a7b8c9d0e1f2a3b4c5d6e
Author: Antonio Barros <antonio@email.com>
Date:   Thu Jun 11 22:30:00 2026 -0300

    Adiciona guia de configuração do Git

```

Informações exibidas:
- Commit: Hash único do commit.
- Author: Quem realizou o commit.
- Date: Data e hora.
- Mensagem: Descrição da alteração.

## formatos 
### Historico resumido:
```bash
git log --oneline 
```
Exemplo:
```
4d7f8a2 Adiciona guia de configuração do Git
8f9a123 Corrige erro de formatação
1a2b3c4 Commit inicial
```

### Mostrar gráfico dos branches:

```bah
git log --oneline --graph
```
Exemplo:
```
* 4d7f8a2 Adiciona guia de configuração do Git
* 8f9a123 Corrige erro de formatação
* 1a2b3c4 Commit inicial
```
quando existe branches e merges:
```
*   9a8b7c6 Merge branch 'feature'
|\
| * 7f6e5d4 Nova funcionalidade
|/
* 4d7f8a2 Commit anterior
```

### Mostrar branches e tags
```bash
git log --oneline --graph --decorate
```
Exemplo:
```
* 4d7f8a2 (HEAD -> main, origin/main) Adiciona guia
* 8f9a123 Corrige erro
* 1a2b3c4 Commit inicial
```

Significado:
- HEAD → Commit atual.
- main → Branch local.
- origin/main → Branch remota no - GitHub.

### Histórico completo mais legível
```bash
git log --oneline --graph --decorate --all
```
um dos formatos mais usados

### Limitar quantidade de commits
mostrando apenas os 5 ultimos
```bash
git log -5
```
ou
```bash
git log --oneline -5
```
### Ver alterações de um commit
```bash
git log -p
```

alem de mostrar commits, motra o que foi modificado 

### Ver quais arquivos foram alterados
```bash
git log --stat
```
Exemplo:
```
README.md | 10 +++++-----
main.py   | 5 +++++

2 files changed, 10 insertions(+), 5 deletions(-)
```
### Histórico de um arquivo específico
```bash
git log README.md
```
mostra apenas commits que modificaram esse arquivo

### filtrar por autor
```bash
git log --author="Antonio Barros"
```
### Filtrar por data
```bash
git log --since="2026-06-01"
```
Ultima semana:
```bash
git log --since="1 week ago"

```
Ultimo mês:
```bash
git log --since="1 month ago"
```

## Ver um commit específico
Usando o hash:
```bash
git show 4d7f8a2
```
ou 
```bash
git log --oneline
```

para encontrar o hash primeiro.

