---
title: 'Erro: O serviço do depurador remoto do Visual Studio no computador de destino não pode se conectar novamente a esse computador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cfd2db1e4bf5b87d12eb5d5ffcf94d06e142516
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471746"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Erro: o serviço Depurador Remoto do Visual Studio no computador de destino não pode se reconectar a este computador
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
  
1.  Verifique se o serviço de depurador remoto do Visual Studio está configurado corretamente no computador remoto. Para obter mais informações, consulte [depuração remota](../debugger/remote-debugging.md).  
  
2.  Execute o serviço de depurador remoto com uma conta que possa acessar o computador host do depurador, conforme mostrado na tabela anterior.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Para adicionar o privilégio “Fazer logon como um serviço”  
  
1.  Sobre o **iniciar** menu, escolha **painel de controle**.  
  
2.  No painel de controle, escolha **exibição clássica**, se necessário.  
  
3.  Clique duas vezes em **Ferramentas Administrativas**.  
  
4.  Na janela de ferramentas administrativas, clique duas vezes em **política de segurança Local**.  
  
5.  No **configurações de segurança Local** janela, expanda o **políticas locais** pasta.  
  
6.  Clique em **atribuição de direitos do usuário**.  
  
7.  No **política** coluna, clique duas vezes em **fazer logon como um serviço** para exibir as atribuições de política de grupo locais atuais no **fazer logon como um serviço** caixa de diálogo.  
  
8.  Para adicionar novos usuários, clique o **adicionar usuário ou grupo** botão.  
  
9. Quando tiver terminado de adicionar usuários, clique em **Okey**.  
  
### <a name="to-work-around-this-error"></a>Para resolver esse erro  
  
-   Execute o Monitor de Depuração Remota como um aplicativo em vez de um serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)