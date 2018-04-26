---
title: Acessando uma região de formulário em tempo de execução
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e1ecc6ce8f3b196ec7395652b8e8584bb9b0b2d9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="accessing-a-form-region-at-run-time"></a>Acessando uma região de formulário em tempo de execução


|Aplica-se a|  
|----------------|  
|As informações neste tópico se aplicam somente aos tipos e versões de projetos do Microsoft Office a seguir. Para obter mais informações, consulte [recursos disponibilizados pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Tipo de projeto**<br /><br /> -Projetos de suplemento do VSTO<br /><br /> **Versão do Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  

 Use o `Globals` classe para regiões de formulário de acesso em qualquer lugar dentro de seu projeto do Outlook. Para obter mais informações sobre o `Globals` de classe, consulte [acesso Global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).  

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  

## <a name="accessing-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Acessando as regiões de formulário que aparecem em uma janela de Inspetor do Outlook específico  
 Para acessar todas as regiões de formulário que aparecem em um inspetor do Outlook específico, chame o `FormRegions` propriedade do `Globals` classe e passar uma <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto que representa o Inspetor.  

 O exemplo a seguir obtém a coleção de regiões de formulário que aparecem no Inspetor de que tem o foco no momento. Neste exemplo, em seguida, acessa uma região de formulário na coleção chamada `formRegion1` e define o texto que aparece em uma caixa de texto para `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  

## <a name="accessing-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Acessando as regiões de formulário que aparecem em uma janela do Pesquisador de objetos específicos do Outlook  
 Para acessar todas as regiões de formulário que aparecem em um navegador específico do Outlook, chame o `FormRegions` propriedade do `Globals` classe e passar uma <xref:Microsoft.Office.Interop.Outlook.Explorer> objeto que representa o Gerenciador.  

 O exemplo a seguir obtém a coleção de regiões de formulário que aparecem no Pesquisador de objetos que tem o foco no momento. Neste exemplo, em seguida, acessa uma região de formulário na coleção chamada `formRegion1` e define o texto que aparece em uma caixa de texto para `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  

## <a name="accessing-all-form-regions"></a>Acessar todas as regiões de formulário  
 Para acessar todas as regiões de formulário que aparece em todos os navegadores e todos os inspetores, chame o `FormRegions` propriedade o `Globals` classe.  

 O exemplo a seguir obtém a coleção de regiões de formulário que aparece em todos os navegadores e todos os inspetores. Neste exemplo, em seguida, acessa uma região de formulário chamada `formRegion1` e define o texto que aparece em uma caixa de texto para `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  

## <a name="accessing-controls-on-a-form-region"></a>Acessando controles em uma região de formulário  
 Para controles de acesso em uma região de formulário usando o `Globals` classe, você deve disponibilizar os controles a código fora do arquivo de código de região de formulário.  

### <a name="form-regions-designed-in-the-form-region-designer"></a>Regiões de formulário projetados no Designer de região de formulário  
 Para c#, altere o modificador de cada controle que você deseja acessar. Para fazer isso, selecione cada controle no designer de região de formulário e altere o **modificadores** propriedade **interno** ou **pública** no **propriedades** janela. Por exemplo, se você alterar o **modificador** propriedade `textBox1` para **interno**, você pode acessar `textBox1` digitando `Globals.FormRegions.FormRegion1.textBox1`.  

 Do Visual Basic, você não precisa alterar o modificador.  

### <a name="imported-form-regions"></a>Regiões de formulário importado  
 Quando você importa uma região de formulário projetada no Outlook, o modificador de acesso de cada controle na região de formulário se torna privado. Porque você não pode usar o designer de região de formulário para modificar uma região de formulário importado, não é possível alterar o modificador de um controle no **propriedades** janela.  

 Para habilitar o acesso a um controle de fora do arquivo de código de região de formulário, crie uma propriedade no arquivo de código de região de formulário para retornar o controle.  

 Para obter mais informações sobre como criar propriedades em c#, consulte [como: declarar e usar propriedades de gravação de leitura &#40;C&#35; guia de programação&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).  

 Para obter mais informações sobre como criar propriedades no Visual Basic, consulte [como: criar uma propriedade (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).  

## <a name="see-also"></a>Consulte também  
 [Diretrizes para criação de regiões de formulário do Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Passo a passo: Criando uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Ações personalizadas em regiões de formulário do Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Associando uma região de formulário uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Passo a passo: Importando uma região de formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Como: impedir a exibição de uma região de formulário do Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)   
 [Acessando a faixa de opções no tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)  
