---
title: 'Como: exibir documentos de Script | Microsoft Docs'
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
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc24c5e9c2332516cbf939e14581a2df7bea44eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468325"
---
# <a name="how-to-view-script-documents"></a>Como exibir documentos de script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: exibir documentos de Script](https://docs.microsoft.com/visualstudio/debugger/how-to-view-script-documents).  
  
Em versões anteriores do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], os arquivos de script do lado do cliente gerados do script do lado do servidor eram exibidos na janela Explorador de Script. A janela Explorador de Script estava geralmente oculta, de modo que a disponibilidade de script do lado do cliente não era sempre óbvia.  
  
 No [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], os arquivos de script do lado do cliente gerados do script do lado do servidor aparecem no Gerenciador de Soluções, que é visível por padrão. A janela Explorador de Script foi eliminada.  
  
 Os arquivos de script do lado do cliente são visíveis apenas quando você está no modo de depuração ou modo de interrupção. Eles aparecem na **documentos de Script** nó.  
  
 Os arquivos de script do lado do servidor são sempre visíveis. Eles aparecem na  **\<nome de caminho do site >** nó. O nome do nó é semelhante a este exemplo: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Para exibir um documento de script do lado do servidor  
  
1.  Na **Gerenciador de soluções**, abra o  **\<nome do caminho do site >** nó.  
  
2.  Clique duas vezes no arquivo de script que deseja exibir.  
  
     O arquivo de script do lado do servidor é aberto em uma janela de origem.  
  
### <a name="to-view-a-client-side-script-document"></a>Para exibir um documento de script do lado do cliente  
  
1.  Na **Gerenciador de soluções**, abra o **documentos de Script** nó.  
  
2.  Clique duas vezes no arquivo de script que deseja exibir.  
  
     O arquivo de script do lado do cliente é aberto em uma janela de origem.  
  
## <a name="see-also"></a>Consulte também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)



