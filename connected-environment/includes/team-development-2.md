2. Pressione F5 (ou digite `vsce up` na janela do terminal) para executar o serviço. Isso fará com que ele seja executado automaticamente no espaço recém-selecionado `scott`. 
1. É possível confirmar essa ação executando `vsce list` novamente. Primeiro, você verá que uma instância de `mywebapi` está em execução no espaço `scott` (a versão em execução no `mainline` ainda está em execução, mas não está listada). Em segundo lugar, a URL de ponto de acesso para o `webfrontend` está prefixada com o texto "scott-". Essa URL é exclusiva para o espaço `scott` e significa que as solicitações enviadas para a “URL scott" tentarão primeiro ser roteadas para os serviços no espaço `scott` e efetuarão fallback para os serviços no espaço `mainline`.

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------
mywebapi     scott     mywebapi-0.1.0     80/TCP  15s ago     http://localhost:61466
webfrontend  mainline  webfrontend-0.1.0  80/TCP  5h ago      https://scott-webfrontend-contosodev.vsce.io
```

![](../media/space-routing.png)

Essa capacidade interna do Connected Environment permite testar o código de ponta a ponta em um ambiente compartilhado, sem precisar que cada desenvolvedor recrie a pilha completa de serviços em seu espaço. Observe que este roteamento exige que cabeçalhos de propagação sejam encaminhados no código do aplicativo, conforme foi ilustrado na etapa anterior deste guia.

## <a name="test-code-in-a-space"></a>Testar o código no espaço
Para testar a nova versão da `mywebapi` em conjunto com o `webfrontend`, abra seu navegador na URL de ponto de acesso público do webfrontend e acesse a página Sobre. Sua nova mensagem deverá ser exibida.

Agora, remova a parte "scott-" da URL e atualize o navegador. O comportamento antigo deverá ocorrer (exibido pela versão da `mywebapi` em execução em `mainline`).