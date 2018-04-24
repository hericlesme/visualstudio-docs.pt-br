---
title: Depurando aplicativos ClickOnce que usam System.Deployment.Application | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30cbf4aab2975b95703c24462604c1a43ed3554c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Depurando aplicativos ClickOnce que usam System.Deployment.Application
Em [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação permite que você configure como um aplicativo é atualizado. No entanto, se você precisar usar e personalizar avançado [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] recursos de implantação, você precisará acessar o modelo de objeto de implantação fornecido pelo <xref:System.Deployment.Application>. Você pode usar o <xref:System.Deployment.Application> APIs para tarefas avançadas, como:  
  
-   Criar uma opção "Atualizar agora" em seu aplicativo  
  
-   Condicional, sob demanda downloads de vários componentes de aplicativo  
  
-   Atualizações integrado diretamente ao aplicativo  
  
-   Garantir que o aplicativo cliente está sempre atualizado  
  
 Porque o <xref:System.Deployment.Application> APIs funcionam apenas quando um aplicativo é implantado com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia, a única maneira de depurá-los é implantar o aplicativo usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], anexar a ela e depurá-lo. Pode ser difícil anexar o depurador antecipada, porque esse código geralmente é executado quando o aplicativo é iniciado e executado antes de você pode anexar o depurador. Uma solução é colocar quebras (ou interrompido, para projetos do Visual Basic) antes do código de verificação de atualização ou o código sob demanda.  
  
 A técnica de depuração recomendada é o seguinte:  
  
1.  Antes de começar, verifique se o símbolo (. PDB) e arquivos de origem são arquivados.  
  
2.  Implante a versão 1 do aplicativo.  
  
3.  Crie uma nova solução em branco. Do **arquivo** menu, clique em **novo**, em seguida, **projeto**. No **novo projeto** caixa de diálogo, abra o **outros tipos de projetos** nó, em seguida, selecione o **soluções do Visual Studio** pasta. No **modelos** painel, selecione **solução em branco**.  
  
4.  Adicione o local de origem arquivados até as propriedades para a nova solução. Em **Solution Explorer**, com o botão direito no nó da solução e clique em **propriedades**. No **páginas de propriedade** caixa de diálogo, selecione **depurar arquivos de origem**, em seguida, adicione o diretório do código-fonte arquivados. Caso contrário, o depurador encontrará os arquivos de origem desatualizadas, desde que os caminhos de arquivo de origem são registrados no arquivo. PDB. Se o depurador usa arquivos de origem desatualizadas, você verá uma mensagem informando que a origem não corresponde.  
  
5.  Verifique se que o depurador pode encontrar os arquivos. PDB. Se você tiver implantado-los com o seu aplicativo, o depurador localiza automaticamente. Sempre parece ao lado do assembly em questão pela primeira vez. Caso contrário, você precisará adicionar o caminho de arquivo para o **símbolo locais de arquivo (. PDB)** (acessem essa opção, o **ferramentas** menu, clique em **opções**, abra o  **Depuração** nó e clique em **símbolos**).  
  
6.  Depurar o que acontece entre o `CheckForUpdate` e `Download` / `Update` chamadas de método.  
  
     Por exemplo, o código de atualização pode ser da seguinte maneira:  
  
    ```  
        Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
            If My.Application.Deployment.IsNetworkDeployed Then  
  
                If (My.Application.Deployment.CheckForUpdate()) Then  
  
                    My.Application.Deployment.Update()  
                    Application.Restart()  
  
                End If  
  
            End If  
        End Sub  
    ```  
  
7.  Implante a versão 2.  
  
8.  Tentativa de anexar o depurador ao aplicativo versão 1, ele baixa uma atualização para a versão 2. Como alternativa, você pode usar o `System.Diagnostics.Debugger.Break` método ou simplesmente `Stop` no Visual Basic. Obviamente, não deixe essas chamadas de método no código de produção.  
  
     Por exemplo, suponha que você está desenvolvendo um aplicativo Windows Forms e você tiver um manipulador de eventos para esse método com a lógica de atualização nela. Para depurar esse problema, basta anexar antes do botão for pressionado, defina um ponto de interrupção (certifique-se de que você abre o arquivo apropriado e defina o ponto de interrupção lá).  
  
 Use o <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> propriedade invocar o <xref:System.Deployment.Application> APIs somente quando o aplicativo é implantado; as APIs não deve ser chamadas durante a depuração em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Deployment.Application>