---
title: "Como: impedir a exibição de uma região de formulário do Outlook | Microsoft Docs"
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
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: def4454f1031e5958dfc10e1a1fc77ccaed59067
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Como evitar que o Outlook exiba uma região de formulário
  Pode haver situações em que você não quer que o Microsoft Office Outlook para exibir uma região de formulário para um determinado item. Por exemplo, se um item de contato não contém um endereço de negócios, você pode impedir que uma região de formulário que mostra a localização dos negócios em um mapa apareça.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Para impedir a exibição de uma região de formulário do Outlook  
  
1.  Abra o arquivo de código para a região de formulário que você deseja modificar.  
  
2.  Expanda o **fábrica de região de formulário** região de código.  
  
3.  Adicione código para o `FormRegionInitializing` manipulador de eventos que define o <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriedade o <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe para **true**.  
  
 Neste exemplo, se o item de contato não contém um endereço, o <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> está definida como **true**, e a região de formulário não é exibida.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)   
 [Passo a passo: Criando uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Passo a passo: Criando uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Instruções passo a passo: importando uma região do formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  