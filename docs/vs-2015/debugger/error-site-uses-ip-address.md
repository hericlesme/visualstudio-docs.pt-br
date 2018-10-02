---
title: 'Erro: O Site usa endereço IP | Microsoft Docs'
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
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93d64f06db4b1f070da4f0963ed879ef64e4cb33
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468149"
---
# <a name="error-site-uses-ip-address"></a>Erro: o site usa endereço IP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [erro: o Site usa endereço IP](https://docs.microsoft.com/visualstudio/debugger/error-site-uses-ip-address).  
  
Esse erro ocorre quando o depurador tenta anexar-se automaticamente a um aplicativo Web que está usando um endereço IP. Isso ocorre se você alterar **identificação de site** à **usar endereço IP específico** no IIS.  
  
 Para que o anexo automático funcione, você precisará criar o projeto com o endereço IP específico em vez de apenas o nome do computador. Caso contrário, o depurador alterará o nome do computador para localhost, o que causará uma falha ao enviar o verbo de depuração para o IIS.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Use a anexação manual em vez disso (no menu Depurar, escolha **anexar ao processo**).  
  
     —ou—  
  
2.  Alterar o **identificação do site da Web do IIS** configuração.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



