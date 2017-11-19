---
title: "Como: adicionar controles à exibição Backstage | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a16c564b39afdc2ec3cf3e15883fc05b2a13f5d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Como adicionar controles à exibição Backstage
  Você pode usar o Designer de faixa de opções para adicionar controles ao menu aberto quando você clica o **arquivo** guia quando você executar o aplicativo, controles que você adicionar à **arquivo** guia aparecerá um grupo chamado  **Suplementos**.  
  
 Você não pode posicionar controles antes ou depois de controles internos usando o designer de faixa de opções no Visual Studio. Um controle interno é um controle que já aparece no modo de exibição Backstage. Se você desejar posicionar controles antes ou depois de controles internos, você deve usar um XML da faixa de opções. Para obter mais informações sobre **da faixa de opções (XML)**, consulte [XML da faixa de opções](../vsto/ribbon-xml.md). Para obter mais informações sobre como personalizar o modo de exibição Backstage, consulte [introdução para o modo de exibição do Office 2010 Backstage para desenvolvedores](http://go.microsoft.com/fwlink/?LinkId=182189) e [personalizar a exibição do Office 2010 Backstage para desenvolvedores](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Para adicionar controles à exibição Backstage  
  
1.  Abra o item de faixa de opções no modo de Design.  
  
     Para obter informações sobre como adicionar um **faixa de opções (Visual Designer)** item ao seu projeto, consulte [como: obter iniciado Personalizando a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  No Designer de faixa de opções, clique o **arquivo** guia.  
  
     Um designer de menu é exibido. Essa superfície de design não contém controles.  
  
3.  Do **controles de faixa de opções do Office** guia do **caixa de ferramentas**, arraste qualquer um dos seguintes controles para o designer de menu:  
  
    -   Botão  
  
    -   CheckBox  
  
    -   Galeria  
  
    -   Menu  
  
    -   Separador  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Arraste os controles para movê-las para novas posições no menu.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Designer de faixa de opções](../vsto/ribbon-designer.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)   
 [Como: personalizar a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Instruções passo a passo: criando uma guia personalizada usando o designer da faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  