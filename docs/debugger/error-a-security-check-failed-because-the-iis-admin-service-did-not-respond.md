---
title: "Erro: Falha de uma verificação de segurança porque o serviço de administração do IIS não respondeu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bc147c979357934d68692ea863c665422c84b34
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Erro: falha na verificação de segurança porque o Serviço de Administração do IIS não respondeu
Esse erro ocorre quando o Serviço de administração do IIS não responde. Isso geralmente indica que há um problema com a instalação do IIS. Primeiro, verifique se o serviço está em execução usando o **serviços** ferramenta de **ferramentas administrativas**.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Reinstale o IIS, usando o **adicionar ou remover programas** painel de controle.  
  
-   -ou-  
  
-   Remova o IIS do computador, usando o painel de controle Adicionar ou Remover Programas. Se você tiver removido o IIS e ainda tiver problemas, verifique no Registro se essa chave já não existe:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     -ou-  
  
-   Desabilite o Serviço de administração do IIS, usando o painel de controle Ferramentas Administrativas. Isso desabilitará o IIS no computador.  
  
     Depois de executar qualquer uma dessas três etapas, reinicie o computador.  
  
     Para obter informações adicionais, consulte a documentação do IIS.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)