---
title: 'Como: responder ao depurador Just-In-Time | Microsoft Docs'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cec8887ddf2023a8abd08f409b93f47efdc7001
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155562"
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Como: responder ao depurador Just-In-Time

As ações que você deve executar quando você vir o Just-in-Time dependem de caixa de diálogo do depurador que você está tentando fazer:

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Se você deseja corrigir ou depurar o erro (usuários do Visual Studio)

- Você deve ter [Visual Studio instalado](http://visualstudio.microsoft.com) para exibir as informações detalhadas sobre o erro e tente depurá-lo. Para obter mais informações, consulte [depurar usando o depurador Just-in-](../debugger/debug-using-the-just-in-time-debugger.md). Se você não pode resolver o erro e corrigir o aplicativo, entre em contato com o proprietário do aplicativo para resolver o erro.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Se você quiser impedir que a caixa de diálogo do depurador Just-in-apareçam

Você pode tomar medidas para evitar o Just-in-Time caixa de diálogo do depurador apareça. Se o aplicativo trata o erro, você pode executar o aplicativo normalmente.

1. (Aplicativos web) Se você estiver tentando executar um aplicativo web, você pode desabilitar a depuração de script.

    Para o Internet Explorer ou Edge, desabilite a depuração de script na caixa de diálogo Opções da Internet. Você pode acessar essas configurações do **painel de controle** > **rede e Internet** > **opções da Internet** (as etapas exatas dependem de seu versão do Windows e do navegador).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    Em seguida, reabra a página da web em que você encontrou o erro. Se a alteração dessa configuração não resolver o problema, contate o proprietário do aplicativo web para corrigir o problema.

3. (Usuários do visual Studio) Se você tiver instalado o Visual Studio (ou se você tiver instalado anteriormente e o removeu), [Just-in-Time de desabilitar a depuração](../debugger/debug-using-the-just-in-time-debugger.md) e tente executar o aplicativo novamente.

    > [!IMPORTANT]
    > Se você desativar o Just-in-Time de depuração e o aplicativo encontra uma exceção sem tratamento (erro), você verá uma caixa de diálogo de erro padrão em vez disso, ou o aplicativo irá falhar ou travar. O aplicativo não será executado normalmente até que o erro seja corrigido (por você ou o proprietário do aplicativo).

2. (ASP.NET e IIS) Se você estiver hospedando um aplicativo Web ASP.NET no IIS, desabilite a depuração do lado do servidor.

    No Gerenciador do IIS, clique com botão direito no nó do servidor e escolha **alternar para exibição de recursos**. Na seção ASP.NET, escolha **compilação do .NET** e, em seguida, certifique-se de escolher **falso** como o comportamento de depuração (as etapas são diferentes em versões anteriores do IIS).

## <a name="see-also"></a>Consulte também
 [Noções básicas do depurador](../debugger/debugger-basics.md)
