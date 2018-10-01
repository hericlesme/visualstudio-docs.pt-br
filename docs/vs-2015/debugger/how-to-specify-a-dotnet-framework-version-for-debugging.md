---
title: 'Como: especificar uma versão do .NET Framework para depuração | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a07975591525f9109fecfbfb5aaa27642fc9562
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464078"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Como especificar uma versão do .NET Framework para depuração
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: especificar um .NET Framework versão para depuração](https://docs.microsoft.com/visualstudio/debugger/how-to-specify-a-dotnet-framework-version-for-debugging).  
  
O depurador do [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] dá suporte a versões anteriores de depuração do Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bem como à versão atual. Se você iniciar um aplicativo do Visual Studio, o depurador sempre poderá identificar a versão correta do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] para o aplicativo que você está depurando. Se o aplicativo já está em execução e usar **anexar**, o depurador pode não ser capaz de identificar uma versão anterior da [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Se isso ocorrer, você receberá uma mensagem de erro, que indica  
  
 O depurador fez uma suposição incorreta sobre a versão do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que seu aplicativo usará.  
  
 Nesses casos raros, você pode definir uma chave do Registro para indicar ao depurador a versão a ser usada.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Para especificar uma versão do .NET Framework para depuração  
  
1.  Examine no diretório Windows\Microsoft.NET\Framework para localizar as versões do .NET Framework instaladas no computador. Os números de versão devem ser semelhantes a:  
  
     `V1.1.4322`  
  
     Identifique o número de versão correta e anote.  
  
2.  Iniciar o **Editor do registro** (regedit).  
  
3.  No **Editor do registro**, abra a pasta HKEY_LOCAL_MACHINE.  
  
4.  Navegue até: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Se a chave não existir, clique com botão direito HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine e clique em **nova chave**. Nomeie a nova chave `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Depois de navegar até {449EC4CC-30D2-4032-9256-EE18EB41B62B}, examine os **nome** coluna e localize a chave CLRVersionForDebugging.  
  
    1.  Se a chave não existir, clique com botão direito {449EC4CC-30D2-4032-9256-EE18EB41B62B} e clique em **novo valor de cadeia de caracteres**. Clique com o novo valor de cadeia de caracteres, clique em **renomeie**e o tipo `CLRVersionForDebugging`.  
  
6.  Clique duas vezes em **CLRVersionForDebugging**.  
  
7.  No **Editar cadeia de caracteres** , digite o número de versão do .NET Framework na **valor** caixa. Por exemplo: V1.1.4322  
  
8.  Clique em **OK**.  
  
9. Fechar o **Editor do registro**.  
  
     Se você ainda receber uma mensagem de erro quando começar a depuração, verifique se inseriu o número de versão corretamente no Registro. Além disso, verifique se está usando uma versão do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] com suporte pelo Visual Studio. O depurador é compatível com a versão atual e a anterior do .NET Framework, mas não é compatível com versões futuras.  
  
## <a name="see-also"></a>Consulte também  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)



