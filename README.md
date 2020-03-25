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



### Puxar alterações feitas no repositório remoto para o repositório local

```
$ git pull
```



## Estado dos Arquivos

- Não monitorado (untracked)
- Modificado (modified) - arquivo que foi modificado
- Preparado (staged) - apoś o git add, os arquivos estão prontos para serem commitados
- Consolidado (commited) - o novo estado do arquivo já está registrado no repositório local



## Contribuições para projetos

