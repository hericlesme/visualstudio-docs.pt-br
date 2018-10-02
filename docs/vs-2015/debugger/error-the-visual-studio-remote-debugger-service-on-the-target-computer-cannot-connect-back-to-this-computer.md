---
title: 'Erro: O serviço de depurador remoto do Visual Studio no computador de destino não pode se reconectar a este computador | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27ae98de5ac5062bd55a3818b82e1f6ba771b612
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475341"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Erro: o serviço Depurador Remoto do Visual Studio no computador de destino não pode se reconectar a este computador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [erro: serviço de depurador remoto a do Visual Studio no computador de destino não pode se reconectar a este computador](https://docs.microsoft.com/visualstudio/debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer).  
  
Esse erro significa que o serviço de depurador remoto do Visual Studio está em execução em uma conta de usuário que não pode autenticar ao tentar se conectar ao computador do qual você está depurando.  
  
 A tabela a seguir mostra quais contas podem acessar o computador:  
  
|||||  
|-|-|-|-|  
||Conta de LocalSystem|Conta de domínio|Contas locais que têm o mesmo nome de usuário e senha nos dois computadores|  
|Ambos os computadores no mesmo domínio|Sim|Sim|Sim|  
|Ambos os computadores em domínios que tenham a confiança bidirecional|Não|Não|Sim|  
|Um ou ambos os computadores em um grupo de trabalho|Não|Não|Sim|  
|Computadores em domínios diferentes|Não|Não|Sim|  
  
 Além disso:  
  
-   A conta na qual você executa o serviço de depurador remoto do Visual Studio deve ser administrador no computador remoto de modo que possa depurar qualquer processo.  
  
-   A conta também deve ser concedida a `Log on as a service` privilégio no computador remoto que está usando o **política de segurança Local** ferramenta administrativa.  
  
-   Se você estiver usando um acesso de conta local no computador, deverá executar o serviço de depurador remoto do Visual Studio em uma conta local.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se o serviço de depurador remoto do Visual Studio está configurado corretamente no computador remoto. Para obter mais informações, consulte [definir configurar as ferramentas remotas no dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
2.  Execute o serviço de depurador remoto com uma conta que possa acessar o computador host do depurador, conforme mostrado na tabela anterior.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Para adicionar o privilégio “Fazer logon como um serviço”  
  
1.  Sobre o **inicie** menu, escolha **painel de controle**.  
  
2.  No painel de controle, escolha **modo de exibição clássico**, se necessário.  
  
3.  Clique duas vezes em **Ferramentas Administrativas**.  
  
4.  Na janela Ferramentas administrativas, clique duas vezes em **política de segurança Local**.  
  
5.  No **configurações de segurança Local** janela, expanda o **políticas locais** pasta.  
  
6.  Clique em **atribuição de direitos do usuário**.  
  
7.  No **diretiva** coluna, clique duas vezes em **fazer logon como um serviço** para exibir as atribuições de política de grupo locais atuais no **fazer logon como um serviço** caixa de diálogo.  
  
8.  Para adicionar novos usuários, clique o **adicionar usuário ou grupo** botão.  
  
9. Quando você terminar de adicionar usuários, clique em **Okey**.  
  
### <a name="to-work-around-this-error"></a>Para resolver esse erro  
  
-   Execute o Monitor de Depuração Remota como um aplicativo em vez de um serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas e erros de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)



