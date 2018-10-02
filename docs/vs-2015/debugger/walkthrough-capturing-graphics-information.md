---
title: 'Passo a passo: Capturando informações de gráficos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de553729d37bb82d1b30c6a142f7e65c983bb1c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462323"
---
# <a name="walkthrough-capturing-graphics-information"></a>Passo a passo: capturando informações de gráficos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [instruções passo a passo: capturando informações de gráficos](https://docs.microsoft.com/visualstudio/debugger/graphics/walkthrough-capturing-graphics-information).  
  
Este passo a passo demonstra como usar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnóstico de gráficos para capturar manualmente as informações gráficas de um aplicativo Direct3D.  
  
 Este passo a passo ilustra essas tarefas:  
  
-   Vinculando o diagnóstico de gráficos para seu aplicativo  
  
-   Capturando informações de gráficos  
  
## <a name="capturing-graphics-information"></a>Capturando informações de gráficos  
 Para usar as ferramentas de diagnóstico de gráficos, primeiro, você precisa capturar as informações gráficas nas quais ele confia. Para habilitar a captura, use o **iniciar diagnóstico** comando para conectar o diagnóstico de gráficos para seu aplicativo quando ele é iniciado.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Para habilitar a captura de informações de gráfico depois de um projeto ou solução é carregada  
  
1.  No [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], carregar um arquivo de projeto ou solução para o aplicativo que você deseja capturar informações de gráficos.  
  
2.  Na barra de ferramentas de diagnóstico de gráficos, escolha **iniciar diagnóstico**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Para habilitar a captura de informações de gráficos sem carregar um projeto ou solução  
  
1.  Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**. O **Abrir projeto** caixa de diálogo é exibida.  
  
2.  Em vez de um arquivo de projeto ou solução, especifique o arquivo executável para o aplicativo que você deseja capturar informações de gráficos e, em seguida, escolha **aberto**.  
  
3.  Na barra de menus, escolha **Debug**, **gráficos**, **iniciar diagnóstico**.  
  
 Depois de iniciar o aplicativo e é quadros de renderização, você pode capturar informações gráficas.  
  
#### <a name="to-capture-graphics-information"></a>Para capturar informações gráficas  
  
-   Na barra de ferramentas de diagnóstico de gráficos, escolha o **capturar** botão. ![Ícone do botão de captura de elementos gráficos](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     -ou-  
  
     Com o aplicativo no foco, pressionar **Print Screen**.  
  
 Cada vez que você capturar informações sobre um quadro, o diagnóstico de gráficos registra os eventos de Direct3D e o estado associado e adiciona esses dados para um log de gráficos. Um novo log de gráficos é criado para cada sessão de diagnóstico de gráficos. Para obter informações sobre logs de gráficos, consulte [visão geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo demonstrou como capturar informações gráficas manualmente. Como próxima etapa, considere esta opção:  
  
-   Aprenda a analisar informações gráficas capturadas usando as ferramentas de diagnóstico de gráficos. Ver [visão geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Consulte também  
 [Capturando informações de gráficos](../debugger/capturing-graphics-information.md)



