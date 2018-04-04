## <a name="sign-in-to-azure"></a>Entrar no Azure
Será necessário entrar no Azure para criar o ambiente de desenvolvimento. Digite o seguinte comando em uma janela do terminal:
```cmd
az login
```

> [!Note]
> Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free).

### <a name="if-you-have-multiple-azure-subscriptions"></a>Se você tiver várias assinaturas do Azure...
Você poderá exibir suas assinaturas, executando: 
```cmd
az account list
```
Localize a assinatura que tem `isDefault: true` na saída JSON.
Se essa não for a assinatura que você deseja usar, altere a assinatura padrão:
```cmd
az account set --subscription <subscription ID>
```
