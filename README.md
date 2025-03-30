# Como criar um gitspace (workspace para repositórios git)

Crie um diretorio com o nome gitspace, e também os diretórios
que serão supervisionados pelo git.
Por exemplo o diretorio com o nome da conta pessoal do git:
.../gitspace/minhaContaPessoal
e o diretorio com o nome da conta profissional do git:
.../gitspace/minhaContaProfissional

No diretorio de usuário `/home/$USER` crie dois arquivos
contendo como sufixo o nome da conta do github,
contendo o seguinte conteudo:

***/home/$USER/.gitconfig-minhaContaPessoal***

```
[user]
email = minhaContaPessoal@email.com
    name = minhaContaPessoal
```

***/home/$USER/.gitconfig-minhaContaProfissional***
```
[user]
    email = minhaContaProfissional@email.com
    name = minhaContaProfissional
```
Agora adicione no arquivo .gitconfig a lógica que vai
realizar controle de uso das chaves ssh

***/home/$USER/.gitconfig***
```
[user]
    email = minhaContaPessoal@email.com
    name = minhaContaPessoal
[includeIf "gitdir:~/gitspace/minhaContaPessoal/"]
	  path = .gitconfig-minhaContaPessoal
[includeIf "gitdir:~/gitspace/minhaContaProfissional/"]
	  path = .gitconfig-minhaContaProfissional
```

No diretorio de usuário `/home/$USER/.ssh/` crie um arquivo com
o nome de config "*sem ponto como prefixo*"
***/home/$USER/.ssh/config*** 
```
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/minhaContaPessoal_ed25519
Host github.com-minhaContaProfissional
    HostName github.com
    User git
    IdentityFile ~/.ssh/minhaContaProfissional_ed25519
    IdentitiesOnly yes
```

Se ainda não tiver as chaves ssh de cada conta, crie 
elas utilizando esse passo a passo aqui:

[github.com/rprojetos/ssh-keygen](https://github.com/rprojetos/ssh-keygen)




## Git - Comandos uteis
### Como criar TAG usando comandos do git
#### lista as tags de um repositorio
> git tag
#### criando uma tag usando a mensagem do ultimo commit
> git tag v1.0.0
#### criando uma tag com uma mensagem padronizada
> git tag v1.0.0 -m "version 1.0.0 of the software..."

#### lista as tags com seu comentarios
> git tag -n

#### enviando a tag para o repositorio remoto
obs.: essa tag "alias" vai apontar para o ultimo commite realizado
> git push origin v1.0.0

#### envia todas as tags que foram criadas para cada commit
> git push  origin --tags


