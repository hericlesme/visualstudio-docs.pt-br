---
title: "Erro: O servidor Web não foi possível localizar o recurso solicitado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 782abbf8a5cb30801bbe6041143e031792ff247a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Erro: o servidor Web não conseguiu localizar o recurso solicitado
Devido aos critérios de segurança, o IIS retornou um erro genérico.  
  
 Uma das possíveis causas é a configuração de segurança do servidor. O IIS 6.0 e versões anteriores usaram um programa complementar, conhecido como URLScan, para filtrar solicitações suspeitas e malformadas. O IIS 7.0 tem a Filtragem de Solicitações incorporada pelo mesmo motivo. Em ambos os casos, a filtragem demasiadamente restritiva pode impedir que o Visual Studio depure o servidor.  
  
 Há várias causas possíveis para esse erro. Algumas das causas mais comuns incluem um problema com a instalação ou a configuração do IIS, a configuração do site ou permissões no sistema de arquivos. Você pode tentar acessar o recurso com um navegador. Dependendo de como o IIS é configurado, você pode ter que usar um navegador local no servidor ou inspecionar o log de erros do IIS para obter uma mensagem de erro detalhada.  
  
 Para obter mais informações sobre como solucionar problemas de IIS, consulte [administração e gerenciamento do IIS](http://go.microsoft.com/fwlink/?LinkId=255872).  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta de segurança UrlScan](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [Erro: o servidor Web foi bloqueado e está bloqueando o verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)