---
title: "Acessando a faixa de opções em tempo de execução | Microsoft Docs"
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
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
ms.assetid: 8a7c7c6d-1a18-4d6b-98ee-e483d41f0cd8
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 347659ce577a532604835f57c4b509553f438dea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-ribbon-at-run-time"></a>Acessando a faixa de opções em tempo de execução
  Você pode escrever código para mostrar, ocultar e modificar a faixa de opções e permitir que os usuários executar o código de controles em um painel tarefa personalizada, o painel de ações ou a região de formulário do Outlook.  
  
 Você pode acessar a faixa de opções usando a `Globals` classe. Para projetos do Outlook, você pode acessar as faixas de opções que aparecem em uma janela do Inspetor do Outlook ou o Outlook Explorer específica.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="accessing-the-ribbon-by-using-the-globals-class"></a>Acessando a faixa de opções usando a classe Globals  
 Você pode usar o `Globals` classe para acessar a faixa de opções em um projeto no nível do documento ou um projeto de suplemento do VSTO em qualquer lugar no projeto.  
  
 Para obter mais informações sobre o `Globals` de classe, consulte [acesso Global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 O exemplo a seguir usa o `Globals` classe para acessar uma faixa de opções personalizada denominada `Ribbon1` e defina o texto que aparece em uma caixa de combinação na faixa de opções para `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  
  
## <a name="accessing-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Acessar uma coleção de faixas de opções que aparecem em uma janela de Inspetor do Outlook específico  
 Você pode acessar uma coleção de faixas de opções que aparecem no Outlook *inspetores*. Um inspetor é uma janela que é aberta no Outlook, quando os usuários executam determinadas tarefas, como a criação de mensagens de email. Para acessar a faixa de opções de uma janela de Inspetor, chame o `Ribbons` propriedade do `Globals` classe e passar uma <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto que representa o Inspetor.  
  
 O exemplo a seguir obtém a coleção de faixa de opções do Inspetor que tem o foco no momento. Neste exemplo, em seguida, acessa uma faixa de opções chamada `Ribbon1` e define o texto que aparece em uma caixa de combinação na faixa de opções para `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  
  
## <a name="accessing-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Acessar uma coleção de faixas de opções que aparecem para um Gerenciador específico do Outlook  
 Você pode acessar uma coleção de faixas de opções que aparecem no Outlook *Explorer*. Um Explorer é a interface do usuário principal do aplicativo (IU) para uma instância do Outlook. Para acessar a faixa de opções de uma janela do Explorer, chame o `Ribbons` propriedade do `Globals` classe e passar uma <xref:Microsoft.Office.Interop.Outlook.Explorer> objeto que representa o Gerenciador.  
  
 O exemplo a seguir obtém a coleção de faixa de opções do Explorer que tem o foco no momento. Neste exemplo, em seguida, acessa uma faixa de opções chamada `Ribbon1` e define o texto que aparece em uma caixa de combinação na faixa de opções para `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Designer de faixa de opções](../vsto/ribbon-designer.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)   
 [Visão geral do modelo de objeto de faixa de opções](../vsto/ribbon-object-model-overview.md)   
 [Passo a passo: Criando uma guia personalizada usando o Designer de faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Passo a passo: Atualizando os controles em uma faixa de opções em tempo de execução](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personalizando uma faixa de opções para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Acessando uma região do formulário no tempo de execução](../vsto/accessing-a-form-region-at-run-time.md)  
  
  