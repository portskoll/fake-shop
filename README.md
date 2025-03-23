# FakeShop - Desafio Kubernetes e CI/CD

Esta aplicação foi criada com o objetivo de ensinar conceitos importantes de **Docker**, **Kubernetes** e **GitHub Actions**. O projeto inclui um pipeline de CI/CD automatizado e um deployment na nuvem utilizando a **Digital Ocean**. 

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
