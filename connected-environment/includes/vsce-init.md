## <a name="initialize-code-for-docker-and-kubernetes-development"></a>Inicializar o código para desenvolvimento no Docker e no Kubernetes
Até agora, temos um aplicativo Web básico que pode ser executado localmente. Agora vamos colocá-lo em contêiner criando ativos que definem o contêiner do aplicativo e como ele será implantado no Kubernetes. Isso é fácil com o Connected Environment: 

1. Inicie o VS Code e abra a pasta `webfrontend`. (Você pode ignorar os avisos padrão para adicionar recursos de depuração ou restaurar o projeto.)
1. Abra o Terminal Integrado no VS Code (usando o menu **Exibição | Terminal Integrado**).
1. Execute este comando (verifique se **webfrontend** é a pasta atual):

```cmd
vsce init --public
```

O comando ```init``` da CLI do Connected Environment gera ativos do Docker e do Kubernetes com configurações padrão:
* `./Dockerfile` descreve a imagem de contêiner do aplicativo e como o código-fonte é criado e executado dentro do contêiner.
* Um [Gráfico do Helm](https://docs.helm.sh) em `./charts/webfrontend` descreve como implantar o contêiner no Kubernetes.

Neste momento, não é necessário entender o conteúdo completo desses arquivos. No entanto, vale a pena destacar que **os mesmos ativos de “configuração como código” do Kubernetes e do Docker podem ser usados desde o desenvolvimento até a produção, proporcionando melhor consistência entre ambientes diferentes.**
 
Um arquivo chamado `./vsce.yaml` também é gerado pelo comando `init` e é o arquivo de configuração do Connected Environment. Ele complementa os artefatos do Docker e do Kubernetes com uma configuração adicional que permite uma experiência de desenvolvimento iterativa no Azure. Por exemplo, o gráfico do Helm padrão não expõe nenhum ponto de extremidade público. No entanto, às vezes é útil abrir um ponto de extremidade público temporariamente durante o desenvolvimento, por exemplo, para testar o código usando um dispositivo móvel ou uma URL de webhook. Um arquivo vsce.yaml criado usando `init --public` substitui os parâmetros padrão do Helm para expor um ponto de extremidade público apenas para o tempo de desenvolvimento.
