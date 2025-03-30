# How to create your gitspace

## Uteis
### TAG
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


