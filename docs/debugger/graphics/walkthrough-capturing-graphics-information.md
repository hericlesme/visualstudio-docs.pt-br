---
title: "Passo a passo: Capturando informações de gráficos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 990385be9d9518826f764a59529a1cff61467506
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-capturing-graphics-information"></a>Passo a passo: capturando informações de gráficos
Este passo a passo demonstra como usar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnóstico de gráficos para capturar manualmente as informações de gráficos de um aplicativo Direct3D.  
  
 Este passo a passo ilustra essas tarefas:  
  
-   Capturando o diagnóstico de gráficos para seu aplicativo  
  
-   Capturando informações de gráficos  
  
## <a name="capturing-graphics-information"></a>Capturando informações de gráficos  
 Para usar as ferramentas de diagnóstico de gráficos, primeiro, você precisa capturar as informações gráficas nas quais ele confia. Para habilitar a captura, use o **iniciar diagnóstico** comando conectar o diagnóstico de gráficos para seu aplicativo quando ele for iniciado.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Para habilitar a captura de informações de gráfico depois de uma solução ou projeto é carregado  
  
1.  Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], carregar um arquivo de projeto ou solução para o aplicativo que você deseja capturar informações de gráficos do.  
  
2.  Na barra de ferramentas de diagnóstico de gráficos, escolha **iniciar diagnóstico**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Para habilitar a captura de informações de gráficos sem carregar um projeto ou solução  
  
1.  Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**. O **Abrir projeto** caixa de diálogo é exibida.  
  
2.  Em vez de um arquivo de solução ou projeto, especifique o arquivo executável para o aplicativo que você deseja capturar informações de gráficos do e, em seguida, escolha **abrir**.  
  
3.  Na barra de menus, escolha **depurar**, **gráficos**, **iniciar diagnóstico**.  
  
 Depois de você iniciar o aplicativo e é quadros de renderização, você pode capturar informações de gráficos.  
  
#### <a name="to-capture-graphics-information"></a>Para capturar informações gráficas  
  
-   Na barra de ferramentas de diagnóstico de gráficos, escolha o **capturar** botão. ![Ícone do botão de captura de elementos gráficos](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     -ou-  
  
     Com o aplicativo em foco, pressione **Print Screen**.  
  
 Cada vez que você capturar informações sobre um período, o diagnóstico de gráficos registra os eventos de Direct3D e estados associados e adiciona esses dados em um log de elementos gráficos. Um novo log de gráficos é criado para cada sessão de diagnóstico de gráficos. Para obter informações sobre logs de gráficos, consulte [visão geral](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo demonstrou como capturar informações de gráficos manualmente. Como próxima etapa, considere esta opção:  
  
-   Aprenda a analisar as informações capturadas gráficos usando as ferramentas de diagnóstico de gráficos. Consulte [visão geral](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Consulte também  
 [Capturando informações de gráficos](capturing-graphics-information.md)