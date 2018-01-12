---
title: 'Como: percorrer registros do banco de dados em uma planilha | Microsoft Docs'
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
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f7e6ea8269401a8b026da2562eff96e50820e0a0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Como percorrer registros do banco de dados em uma planilha
  O procedimento a seguir mostra como usar o designer para exibir um único campo de uma tabela de banco de dados em uma planilha do Microsoft Office Excel, com controles que permitem que o usuário final percorrer todos os registros.  
  
 Você pode usar o designer somente no nível de documento. No entanto, você também pode adicionar controles e associá-las aos dados por meio de programação em tempo de execução. Para obter mais informações, consulte [passo a passo: associação de dados simples no VSTO suplemento projeto](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>Para percorrer registros do banco de dados em uma planilha  
  
1.  Abra um projeto de aplicativo do Excel no Visual Studio.  
  
2.  Abra o **fontes de dados** janela e criar uma fonte de dados do banco de dados. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).  
  
3.  Expanda a tabela que contém os dados que você deseja exibir e selecione a coluna específica.  
  
4.  Abra a lista de controles e selecione **NamedRange**.  
  
5.  Arraste o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle para a célula onde você deseja exibir os dados.  
  
6.  Do **Windows Forms** guia do **caixa de ferramentas**, adicione um <xref:System.Windows.Forms.BindingNavigator> controlar à sua planilha e configurar os controles que você deseja usar. Para obter mais informações, consulte [visão geral do controle BindingNavigator &#40; Formulários do Windows &#41; ](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Consulte também  
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  