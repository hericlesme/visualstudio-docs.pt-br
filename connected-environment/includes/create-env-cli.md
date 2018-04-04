## <a name="create-a-kubernetes-development-environment-in-azure"></a>Criar um ambiente de desenvolvimento do Kubernetes no Azure
Com o Connected Environment, você pode criar ambientes baseados no Kubernetes totalmente gerenciados pelo Azure e otimizados para desenvolvimento. O comando cria um ambiente chamado `mydevenvironment` em `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Locais com suporte: `eastus`, `westeurope`

> [!Note]
> Este comando leva cerca de seis minutos. É possível continuar este guia sem esperar.
