---
title: 'Como: responder ao depurador Just-In-Time | Microsoft Docs'
ms.custom: 
ms.date: 05/23/17
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: "48"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8c954cd95da7b6dd2ba0c2938852b939ae396525
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Como: responder ao depurador Just-In-Time

As ações que você deve tomar quando você vir Just-in-Time dependem de caixa de diálogo do depurador que você está tentando fazer:

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Se você deseja corrigir ou depurar o erro (usuários do Visual Studio)

- Você deve ter [Visual Studio instalado](https://www.microsoft.com/en-us/download/details.aspx?id=48146) para exibir informações detalhadas sobre o erro e tente depurá-lo. Para obter mais informações, consulte [depurar usando o depurador Just-in-](../debugger/debug-using-the-just-in-time-debugger.md). Se você não pode resolver o erro e corrigir o aplicativo, contate o proprietário do aplicativo para resolver o erro.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Se você quiser impedir que a caixa de diálogo do depurador Just-in-aparecendo

Você pode adotar medidas para impedir que o Just-in-Time caixa de diálogo de depurador apareça. Se o aplicativo trata o erro, você pode executar o aplicativo normalmente.

1. (Aplicativos da web) Se você estiver tentando executar um aplicativo web, você pode desabilitar a depuração de script.

    Para o Internet Explorer ou borda, desabilite a depuração de script na caixa de diálogo Opções da Internet. Você pode acessar essas configurações do **painel de controle** > **rede e Internet** > **opções da Internet** (as etapas exatas dependem de seu versão do Windows e do navegador).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    Em seguida, reabra a página da web em que você encontrou o erro. Se a alteração dessa configuração não resolver o problema, contate o proprietário do aplicativo web para corrigir o problema.

3. (Usuários do visual Studio) Se você tiver instalado o Visual Studio (ou se você tiver instalado anteriormente e removido), [depuração Just-in-Time de desabilitar](../debugger/debug-using-the-just-in-time-debugger.md) e tente executar o aplicativo novamente.

    > [!IMPORTANT]
    > Se você desabilitar Just-in-Time depuração e o aplicativo encontra uma exceção sem tratamento (erro), você pode ver uma caixa de diálogo de erro padrão em vez disso, ou o aplicativo irá falhar ou suspensão. O aplicativo não será executado normalmente até que o erro seja corrigido (por você ou o proprietário do aplicativo).

2. (ASP.NET e IIS) Se você estiver hospedando um aplicativo da Web do ASP.NET no IIS, desabilite a depuração no lado do servidor.

    No Gerenciador do IIS, clique com botão direito no nó do servidor e escolha **alternar para exibição de recursos**. Na seção de ASP.NET, escolha **compilação do .NET** e, em seguida, verifique se você escolher **False** como o comportamento de depuração (as etapas são diferentes em versões anteriores do IIS).
  
## <a name="see-also"></a>Consulte também    
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
