# Comandos úteis GIT

- Instalar git no Linux:

```
$ sudo apt install git
```



### Configurações de usuário

- Nome:

```
$ git config --global user.name "Seu Nome"
```

- E-mail:

```
$ git config --global user.email "seuemail@algumacoisa"
```

- Editor de texto:

```
$ git config --global core.editor nomeEditorConformeRegrasGit
```



**Visualizar informações sobre o usuário git existente na máquina:**

```
$ git config user.name
```

```
$ git config user.email
```

- Tudo:

```
$ git config --list
```



### Quando precisar de ajuda:

```
$ git help comandoEscolhido
```

- Para visualiza todos os comandos:

```
$ git help
```



### Iniciar primeiro repositório:

(todas configurações do repositório ficam na pasta **.git** existente dentro do repositório).

``` 
$ git init
```



### Após ter realizado alguma modifição em uma pasta ou arquivo:

Serve para informar ao git sobre as modificações que foram realizadas.

```
$ git add nomeArquivo
```

- Para adicionar todos os arquivos do diretório atual:

```
$ git add *
-- ou --
$ git add .
```

- Para visualizar como está o estado do repositório no momento:

```
$ git status
```



### Criar uma versão do seu código fonte

```
$ git commit -am "mensage do que você fez"
```



- Visualizar as modificações realizadas em cima da versão anterior caso haja (mostra quando a as novas modificações não foram commitadas):

```
$ git diff
```

- Visualizar os arquivos que foram modificados desde a ultima versão, caso haja:

```
$ git diff --name-only
```

- Visualizar as modificações realizadas um commit atrás:

```
$ git diff HEAD~1
```

- Visualizar a diferença entre dois commits:

```
$ git diff númeroCommit1 númeroCommit2
```



### Visualizar commits anteriores

```
$ git log
```

- Visualizar quais alterações foram feitas em determinado commit:

```
$ git show númeroDoCommit
```



### Enviar versão para repositório remoto (GitHub)

Adicionar endereço URL do repositório remoto criado no GitHub em projeto local onde o git já foi iniciado (linkar o repositório local com o repositório remoto).

```
$ git remote add origin https://github.com/USUÁRIO/REPOSITÓRIO_CRIADO_NO_GITHUB.git
```

- Enviar a ultima versão para o repositório remoto, (comando completo na primeira vez, apos pode ser somente git push):

```
$ git push -u origin master
```

- Visualizar com qual repositório remoto o projeto está vinculado:

```
$ git remote -v
```



## Estado dos Arquivos

- Não monitorado (untracked)
- Modificado (modified) - arquivo que foi modificado
- Preparado (staged) - apoś o git add, os arquivos estão prontos para serem commitados
- Consolidado (commited) - o novo estado do arquivo já está registrado no repositório local



## Contribuições para projetos

- Para baixar um repositório remoto (baixa uma cópia):

```
$ git clone repositórioURL
```



### Puxar alterações feitas no repositório remoto para o repositório local

Baixa somente as alterações do repositório remoto, mantém o repositório sincronizado com os últimos commits de uma branch "ramo", "ramificação".

```
$ git pull
```



Quando você adiciona um colaborador ao seu repositório remoto significa que ele poderá realizar push's enviando alterações para o repositório remoto.



### Navegar no histórico

- Visualizar como um arquivo ou todo o repositório estava em um determinado commit (o conteúdo volta ao estado que era no commit, porem você não pode fazer novos commits em cima desse estado):

```
$ git checkout numeroCommit nomeArquivoOpicional
```

- Voltar para a master:

```
$ git checkout master
```



### Desfazendo alterações

- Desfaz alterações que não foram adicionadas "add" ainda, voltando para o estado do último commit ou add:

```
$ git checkout -- arquivoOuPasta
--ou--
$ git checkout -- .
```

- Desfazer alterações que já foi realizado o add "staged":

```
$ git checkout HEAD -- nomeArquivo
```

- Desfazer um commit antigo (irá criar um novo commit que desfaz as alterações do commit especificado):

```
$ git revert númeroCommit
```

- Resetar o repositório para um determinado commit (só utilizar se ainda não foi feito git push, os commits acima serão apagados):

```
$ git reset númeroCommit
```

- Resetar voltando commits atrás (commits acima serão apagados, o conteúdo não, ficará como modificado "modified"):

```
$ git reset HEAD~1
--ou--
$ git reset HEAD~outroNúmero
```

- Resetar voltando o estado do commit anterior, apaga o commit e as alterações:

```
$ git reset HEAD~1 --hard
```



### Conflitos

Podem acontecer ao unirmos alterações, quando versões diferentes possuem as mesmas linhas no mesmo arquivo editadas diferentes. Ao resolver conflitos deve ser realizado um commit.



#### Resolvendo conflitos com merge - commit de merge

Ir até o(s) arquivo(s) onde há conflito e apagar as linhas criadas pelo git, informando sobre o conflito, após realizar add e commit.



### Branching

- É uma lista de commits;
- Representa ramificações no repositório;
- Útil em em projetos colaborativos e em equipe;
- Branchs facilitam no processo de desenvolvimento;
- Branch Master é a padrão.



- Visualizar as branchs existentes no repositório:

```
$ git branch
```

- Criar uma branch:

```
$ git branch nomeDaBranch
```

- Excluir uma branch:

```
$ git branch -d nomeDaBranch
```

- Mudar de branch (o repositório passa a ter os commits existentes na branch e novos commits serão adicionados à ela):

```
$ git checkout nomeDaBranch
```

- Criar uma branch e já mudar para ela:

```
$ git checkout -b nomeDaBranch
```

- Criar uma nova branch e enviar para o repositório remoto (GitHub):

```
$ git push -u origin nomeDaBranch
```



### Merge

- Aplica os commits de uma branch na branch atual;
- Encontra um commit comum entre as branchs e aplica todos os commits que a branch atual não possui;
- Caso exista commits na branch atual que não estão na outra branch, será criado commit de merge.



- Comando, (caso haja conflito, resolver o conflito e realizar add e commit após o merge):

```
$ git merge nomeDaBranch
```



### Rebase

- Semelhante ao Merge, porem é diferente na ordem de aplicação dos commits;
- No rebase sus commits à frente da base "ponto em que houve ramificação" são removidos temporariamente, os commits de outra branch são aplicados a branch atual e finalmente os commits removidos temporariamente são aplicados um a um;
- Pode acontecer conflitos que devem ser resolvidos para cada commit;
- É util para evitar mutias ramificações no histórico, utilizar Rebase para pequenas alterações e Merge para grandes alterações;



- Comando:

```
$ git rebase nomeDaBranch
```

- Caso ocorra conflitos, após resolve-los:

```
$ git rebase --continue
```



### Fetch

- Baixa atualizações existentes no repositório remoto, porem não aplica no repositório local;
- Permite fazer o rebase de uma branch em vez de merge;
- Pull = Fetch + Merge;
- Rebase e Fetch contribui para um melhor histórico do projeto.



- Comando (após isso pode-se utilizar o rebase para adicionar as modificações):

```
$ git fetch
```



### Tag

- Útil para definir versões estáveis do projeto (nomear versões como exemplo: v1.0);
- Semelhante a branch, porém não recebe mais commits;
- Guarda um estado do repositório.



- Comando:

```
$ git tag nomeDaTag
```

- Visualizar as tags:

```
$ git tag
```

- Enviar tag para GitHub (lá pode ser encontrado em releases):

```
$ git push origin nomeDaTag
```

- Entrar em uma tag:

```
$ git checkout nomeDaTag
```



# GitHub - Contribuir em projeto

Realizar um Fork no repositório criado por outra pessoa, o fork cria uma cópia do estado atual de um repositório de outra pessoa para o seu usuário.

Issues - para reportar bugs ou tarefas a serem realizadas.

Pull Request - Serve para solicitar que suas alterações sejam unidas a uma branch no mesmo repositório ou a um repositório que sofreu fork. Útil para trabalho colaborativo.

