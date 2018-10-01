---
title: Como especificar o binário para iniciar | Microsoft Docs
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
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec65dd3a5bcc812ff2f7c42ae4cbbba6080664db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466594"
---
# <a name="how-to-specify-the-binary-to-start"></a>Como especificar o início do binário
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: especificar o início do binário](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-the-binary-to-start).  
  
Para analisar binários, como DLLs, você deve inserir informações na caixa de diálogo **\<Destino> Páginas de Propriedade**. Essa informação indica onde o projeto DLL pode localizar o aplicativo de chamada.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Para especificar o executável para iniciar  
  
1.  No **Gerenciador de Desempenho**, clique com o botão direito do mouse no binário de destino e, em seguida, clique em **Propriedades**.  
  
2.  Na caixa de diálogo **Páginas de Propriedades**, clique nas propriedades de **Inicialização**.  
  
3.  Selecione a caixa de seleção **Substituir as propriedades de projeto**.  
  
4.  Na caixa de texto **Executável a Ser Iniciado**, especifique o local do arquivo.  
  
5.  Na caixa de texto **Argumentos**, especifique os argumentos que são necessários para iniciar o aplicativo.  
  
6.  Na caixa de texto **Diretório de Trabalho**, especifique o local do diretório.  
  
7.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)



