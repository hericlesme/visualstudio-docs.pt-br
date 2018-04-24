---
title: 'Como: especificar uma versão do .NET Framework para depuração | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2cb8da54b53814e7f044c67855e8071c627cf2e1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Como especificar uma versão do .NET Framework para depuração
O depurador do [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] dá suporte a versões anteriores de depuração do Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bem como à versão atual. Se você iniciar um aplicativo do Visual Studio, o depurador sempre poderá identificar a versão correta do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para o aplicativo que você está depurando. Se o aplicativo já está em execução e você usar **anexar a**, o depurador pode não ser capaz de identificar uma versão mais antiga do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Se isso ocorrer, você receberá uma mensagem de erro, que indica  
  
 O depurador fez uma suposição incorreta sobre a versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que seu aplicativo usará.  
  
 Nesses casos raros, você pode definir uma chave do Registro para indicar ao depurador a versão a ser usada.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Para especificar uma versão do .NET Framework para depuração  
  
1.  Examine no diretório Windows\Microsoft.NET\Framework para localizar as versões do .NET Framework instaladas no computador. Os números de versão devem ser semelhantes a:  
  
     `V1.1.4322`  
  
     Identifique o número de versão correta e anote.  
  
2.  Iniciar o **Editor do registro** (regedit).  
  
3.  No **Editor do registro**, abra a pasta HKEY_LOCAL_MACHINE.  
  
4.  Navegue até: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Se a chave não existir, clique com botão direito HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine e clique em **nova chave**. Nomeie a nova chave `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Depois de navegar até {449EC4CC-30D2-4032-9256-EE18EB41B62B}, examinar o **nome** coluna e localize a chave CLRVersionForDebugging.  
  
    1.  Se a chave não existir, clique {449EC4CC-30D2-4032-9256-EE18EB41B62B} e clique em **novo valor de cadeia de caracteres**. Clique com o novo valor de cadeia de caracteres, clique em **Renomear**e o tipo `CLRVersionForDebugging`.  
  
6.  Clique duas vezes em **CLRVersionForDebugging**.  
  
7.  No **Editar cadeia de caracteres** , digite o número da versão do .NET Framework para o **valor** caixa. Por exemplo: V1.1.4322  
  
8.  Clique em **OK**.  
  
9. Fechar o **Editor do registro**.  
  
     Se você ainda receber uma mensagem de erro quando começar a depuração, verifique se inseriu o número de versão corretamente no Registro. Além disso, verifique se está usando uma versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] com suporte pelo Visual Studio. O depurador é compatível com a versão atual e a anterior do .NET Framework, mas não é compatível com versões futuras.  
  
## <a name="see-also"></a>Consulte também  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)