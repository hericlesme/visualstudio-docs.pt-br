---
title: 'Aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou você não tiver certeza, não anexe a esse processo | Microsoft Docs'
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
- vs.debug.attachsecuritywarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b856ac3a61d8af72d78546948bbe4ab780e9512e
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2018
ms.locfileid: "47587380"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou, se você não tiver certeza, não anexe a esse processo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou você não tiver certeza, não anexe a esse processo](https://docs.microsoft.com/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process).  
  
Essa caixa de diálogo de aviso é exibida quando você anexa a um processo que contém o código parcialmente confiável ou seja de propriedade de um usuário não confiável imediatamente antes de ocorrer a anexação. Um processo não confiável que contém o código mal-intencionado tem o potencial de danificar o computador que faz a depuração. Se você tem razão para desconfiar do processo e, em seguida, você deve clicar em **Cancelar** para evitar a depuração.  
  
 Para suprimir esse aviso ao depurar um cenário legítimo, feche o Visual Studio e defina o valor dessa chave do registro como 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`e, em seguida, reinicie o Visual Studio. Depois de concluir a depurar do cenário, redefina o valor como 0 e reinicie o Visual Studio.  
  
 Os “Usuários confiáveis” incluem você, mais um conjunto de usuários padrão que são definidos normalmente em computadores que têm o .NET Framework instalado, por exemplo, `aspnet`, `localsystem`, `networkservice` e `localservice`.  
  
## <a name="uielement-list"></a>Lista UIElement  
 Nome  
 Nome do assembly solicitado para depurar  
  
 User  
 Usuário atual  
  
 Attach  
 Pressione para continuar a depurar anexando  
  
 Não anexar  
 Não anexar ao processo  
  
## <a name="see-also"></a>Consulte também  
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Segurança do depurador](../debugger/debugger-security.md)



