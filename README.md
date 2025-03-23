# FakeShop - Desafio Kubernetes e CI/CD

Esta aplicação foi criada com o objetivo de ensinar conceitos importantes de **Docker**, **Kubernetes** e **GitHub Actions**. O projeto inclui um pipeline de CI/CD automatizado e um deployment na nuvem utilizando a **Digital Ocean**. 

Ele possue um banco de dados que será criado e configurado automaticamente dentro de um Pod pelo Kubernetes e possue as variaveis de amabiente que você poderá modificar no arquivo k8s\deployment.yaml, esse arquivo possui toda istruções para a criação dos pods, services, deployment e replicasets que são criados pelos kubernetes.

## Variável de Ambiente
DB_HOST	=> Host do banco de dados PostgreSQL.

DB_USER => Nome do usuário do banco de dados PostgreSQL.

DB_PASSWORD	=> Senha do usuário do banco de dados PostgreSQL.

DB_NAME	=>	Nome do banco de dados PostgreSQL.

DB_PORT	=>	Porta de conexão com o banco de dados PostgreSQL.



## Para criar seu ambiente de desenvolvimento no windows vai precisar:
### Instale o Docker no seu computador
    # Procure no google por kubectl install
    # Você poderá usar o kubectl que o Docker desktop que ja vem instalado
    # va até o site do K3d e veja como instalar o K3d na sua maquina
    # Instale o K3d

## Objetivos
- Demonstrar o uso de Docker para criação e envio de imagens.
- Aplicar conceitos de Kubernetes para orquestração de containers.
- Implementar pipelines automatizados com GitHub Actions.
- Facilitar o aprendizado para interessados através de forks e deploys independentes.

## Como Usar
### Fork do Repositório
1. Faça um **fork** deste repositório clicando no botão "Fork" no GitHub.
2. Clone o repositório forkado para sua máquina local:
   ```bash
   git clone https://github.com/<seu-usuario>/fake-shop-desafio.git

## Configuração de Secrets no GitHub
Para realizar o deploy automático, você deve configurar as secrets no GitHub do seu repositório e ja ter criado um Kubernetes Clusters na Digital Ocean e baixado o arquivo config:

## Secrets Necessários:

DOCKERHUB_USERNAME: Seu nome de usuário no Docker Hub.

DOCKERHUB_TOKEN: Token de autenticação gerado no Docker Hub.

K8S_KUBECONFIG: Arquivo de configuração Kubernetes gerado pelo deployment na Digital Ocean.

## Adicione esses valores nas secrets:

No GitHub, acesse a aba Settings do seu repositório.

Clique em Secrets and variables > Actions.

Adicione os valores necessários.

## Deploy na Digital Ocean
A aplicação foi projetada para deploy na Digital Ocean, mas pode ser adaptada para outros provedores de nuvem como Azure. Se você optar pela Digital Ocean:

Pegue o arquivo de configuração (config) gerado pelo Kubernetes na Digital Ocean.

Adicione o conteúdo do arquivo como valor na secret K8S_KUBECONFIG.

## GitHub Actions
Pipeline CI/CD
O pipeline GitHub Actions é dividido em dois jobs:

CI:

Obtém o código.

Faz login no Docker Hub.

Constrói e envia a imagem Docker para o Docker Hub.

CD:

Configura o Kubernetes usando o arquivo de configuração.

Faz o deployment da aplicação.

Esse pipeline será executado automaticamente ao:

Realizar um push na branch main.

Disparar manualmente pelo workflow_dispatch.

Modificações para Outro Provedor
Caso prefira usar Azure ou outro provedor de nuvem:

Ajuste os steps do job CD para utilizar os comandos e configurações específicos do provedor.

Substitua as configurações de Kubernetes conforme necessário.

Contribuições
Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou submeter pull requests.

## Licença
Este projeto é licenciado por https://devopspro.com.br
Entre em contato com esse time e obtenha mais conhecimento sobre o assunto

Esperamos que você aproveite esta aplicação e aprenda os conceitos de Docker, Kubernetes e GitHub Actions com facilidade! 🚀

## Alguns comandos que irão te auxiliar:
    # Para criar o cluster kubernete simples
    k3d cluster create

    # ver os nodes criados
    kubectl get nodes

    # ver os clusters criados
    k3d cluster list

    #verificar os containers criados pelo K3d
    docker containers ls

    # deletar o cluster criado
    k3d cluster delete

    # criando um cluster kubernetes com servers e agents
    k3d cluster create --servers 3 --agents 3

    # aplicando o deployment
    kubectl apply -f k8s/deployment.yaml

    # verificar se o pod esta rodando
    kubectl get pod

    # testar a aplicação  pegue o nome do pod por esse comando : kubectl get pod
    kubectl port-forward pod/fakeshop-74577d9d88-bkfqj 5000:5000

    # ver o log da aplicação dentro do pod
    fakeshop-74577d9d88-bkfqj

    # apagar o apply
    kubectl delete -f k8s/deployment.yaml

    # olhando os services estão rodando
    kubectl get service

    #olhando a criação do deployment
    kubectl get deployment

    # olhando os replica sets
    kubectl get replicaset

    #olhando todos
    kubectl get all

    #deletando um pod 
    kubectl delete pod/fakeshop-545dcf876f-szjqk

    #verificando os nós do POD
    kubectl get pod -o wide

    #Criando us clusters com apontamento de posta externa para acessar a aplicação
    k3d cluster create --servers 3 --agents 3 -p "5000:30000@loadbalancer"

    #para fazer o rollback da aplicação - olhando as versões
    kubectl rollout history deployment fakeshop

    #fazendo o rollback e acompanhando a recriação dos pods
    kubectl rollout undo deployment fakeshop

    #apagando 0s serviços e pods criados pelo deployment.yaml
    kubectl delete -f k8s/deployment.yaml
