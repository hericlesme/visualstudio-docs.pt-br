---
title: "Como: adicionar um iniciador de caixa de diálogo a um grupo de faixa de opções | Microsoft Docs"
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
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 49dee3d090e2b7f985fd85a6061dea3a2c204e4a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Como adicionar um iniciador da caixa de diálogo a um grupo de faixas de opções
  Você pode adicionar um iniciador de caixa de diálogo a qualquer grupo em uma faixa de opções. Um iniciador de caixa de diálogo é um pequeno ícone que aparece em um grupo. Os usuários clique nesse ícone para abrir caixas de diálogo relacionadas ou painéis de tarefas que fornecem mais opções relacionadas ao grupo.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Para adicionar um iniciador de caixa de diálogo para um grupo de faixa de opções  
  
1.  Selecione o arquivo de código da faixa de opções (arquivo. vb ou. cs) no **Gerenciador de soluções**.  
  
2.  Sobre o **exibição** menu, clique em **Designer**.  
  
3.  No Designer de faixa de opções, clique em qualquer grupo e, em seguida, clique em **DialogBoxLauncher adicionar**.  
  
     Adicione código para o <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> eventos do grupo para abrir a caixa de diálogo interna ou personalizada.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Acessando a faixa de opções em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Designer de faixa de opções](../vsto/ribbon-designer.md)   
 [Visão geral do modelo de objeto de faixa de opções](../vsto/ribbon-object-model-overview.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)   
 [Como: exportar uma faixa de opções do Designer de faixa de opções de XML da faixa de opções](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Como: alterar a posição de uma guia na faixa de opções](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Como: personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md)   
 [Como: adicionar controles à exibição Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Personalizando uma faixa de opções para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Como: personalizar a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Como: Mostrar erros de Interface do usuário do suplemento](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Passo a passo: Criando uma guia personalizada usando o Designer de faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Passo a passo: Atualizando os controles em uma faixa de opções em tempo de execução](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Instruções passo a passo: criando uma guia personalizada usando o XML da faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  