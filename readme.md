# Guia de Configuração

Este repositório contém arquivos YAML para configurar e implantar dois serviços em um cluster Kubernetes: uma API de farmácia e um banco de dados MySQL.

## Arquivos YAML

1. **api-pod.yaml**: Este arquivo define um pod para a API de farmácia. Ele especifica um contêiner com a imagem `rodrigophpweb/app-farma:1.0:latest`, que expõe a porta `8080`. Ele também faz referência a um ConfigMap chamado `db-configmap` para obter variáveis de ambiente relacionadas ao banco de dados.

2. **bd-pod.yaml**: Este arquivo define um pod para o banco de dados MySQL. Ele especifica um contêiner com a imagem `mysql:latest`, que expõe a porta `3306`. Ele também faz referência ao mesmo ConfigMap `db-configmap` para configurar as variáveis de ambiente relacionadas ao banco de dados.

3. **db-configmap.yaml**: Este arquivo define um ConfigMap chamado `db-configmap`, que contém as variáveis de ambiente necessárias para configurar o banco de dados, como o nome do banco de dados, usuário, senha e host.

4. **svc-api.yaml**: Este arquivo define um serviço do tipo NodePort chamado `svc-api` para a API de farmácia. Ele encaminha o tráfego para os pods que correspondem ao rótulo `app: api-pod` na porta `8080`, com um nodePort definido como `30001`.

5. **svc-db.yaml**: Este arquivo define um serviço do tipo ClusterIP chamado `svc-db` para o banco de dados MySQL. Ele encaminha o tráfego para os pods que correspondem ao rótulo `app: db-pod` na porta `3306`.

## Como Usar

Para implantar esses recursos em um cluster Kubernetes, você pode usar o seguinte comando:

```bash
kubectl apply -f <nome-do-arquivo.yaml>
