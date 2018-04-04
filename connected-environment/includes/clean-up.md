## <a name="clean-up"></a>Limpar
Para excluir completamente um Connected Environment do Azure, incluindo todos os serviços em execução que ele contém, use o comando `vsce env rm`. Tenha em mente que essa ação é irreversível.

O exemplo a seguir lista os Connected Environments em sua assinatura ativa do Azure e, em seguida, exclui o ambiente chamado 'myenv' que está no grupo de recursos 'myenv-rg'.

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

