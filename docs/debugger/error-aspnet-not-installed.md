---
title: "Erro: ASP.NET não instalado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec590a018e102e6ab3dd8d2607d9720991e9f90
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-aspnet-not-installed"></a>Erro: ASP.NET não instalado
Esse erro ocorre quando o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] não está instalado corretamente no computador que você está tentando depurar. Isso pode significar que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nunca foi instalado ou que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] foi instalado primeiro e o IIS foi instalado posteriormente.  
  
### <a name="to-reinstall-aspnet"></a>Para reinstalar o ASP.NET  
  
1.  De uma janela de prompt de comando, execute o seguinte comando:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     onde *versão* representa o número de versão do .NET Framework instalado no seu computador, como v1.0.370. Você pode determinar a versão do framework examinando o `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    >  Com o Windows Server 2003, você pode instalar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando **adicionar ou remover programas** no painel de controle.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)