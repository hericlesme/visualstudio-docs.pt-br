---
title: "Personalizando uma faixa de opções para InfoPath | Microsoft Docs"
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
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
ms.assetid: 498c6457-679a-46f2-939f-c0597a17b7ec
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3f4612b3e8dc272b0f51bae80d66d8afe97938e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-a-ribbon-for-infopath"></a>Personalizando uma faixa de opções para InfoPath
  Quando você personaliza a faixa de opções no Microsoft Office InfoPath, você deve considerar onde a faixa de opções personalizada será exibida no aplicativo. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]pode exibir a faixa de opções os seguir três tipos de janelas de aplicativo do InfoPath:  
  
-   Janelas que exibem um modelo de formulário é aberto no modo de design.  
  
-   Janelas que exibem um formulário que é baseado em um modelo.  
  
-   A janela de visualização de impressão.  
  
 **Aplica-se a:** as informações neste tópico se aplicam a projetos de suplemento do VSTO para InfoPath 2010. Para obter mais informações, consulte [recursos disponibilizados pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Usuários e designers de abrem um modelo de formulário no modo de design para modificar a aparência e o layout do modelo. Os usuários abrem formulários com base em um modelo de formulário para adicionar conteúdo.  
  
 A janela de visualização de impressão habilita os designers e os usuários visualizar as páginas de um formulário ou o modelo antes de eles imprimem-los.  
  
> [!NOTE]  
>  O **AddIns** guia não aparece na janela de visualização de impressão. Se você quiser uma guia personalizada seja exibido na janela de visualização de impressão, verifique se o **OfficeId** propriedade da guia não está definida como **TabAddIns**.  
  
 Você deve especificar o tipo de faixa de opções de cada janela no qual você deseja que apareça da faixa de opções.  
  
## <a name="specifying-the-ribbon-type-in-the-ribbon-designer"></a>Especifica o tipo de faixa de opções no Designer de faixa de opções  
 Se você estiver usando o **faixa de opções (Visual Designer)** item, clique no **RibbonType** propriedade da faixa de opções no **propriedades** janela e, em seguida, selecione qualquer uma das IDs de faixa de opções descrito na tabela a seguir.  
  
|ID da faixa de opções|Janela em que a faixa de opções será exibida quando você executar o projeto|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Janelas que exibem um modelo de formulário é aberto no modo de design.|  
|**Microsoft.InfoPath.Editor**|Janelas que exibem um formulário que é baseado em um modelo.|  
|**Microsoft.InfoPath.PrintPreview**|A janela de visualização de impressão.|  
  
 Você pode adicionar mais de uma faixa de opções para um projeto. Se mais de uma faixa de opções compartilharem uma ID de faixa de opções, substituir o método CreateRibbonExtensibilityObject o `ThisAddin` classe do seu projeto para especificar quais faixa de opções para exibir em tempo de execução. Para obter mais informações, consulte [visão geral da faixa de opções](../vsto/ribbon-overview.md).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Especificando o tipo de faixa de opções usando o XML da faixa de opções  
 Se você estiver usando o **da faixa de opções (XML)** item, verifique o valor do *ribbonID* parâmetro o <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> método e retorne a faixa de opções apropriada.  
  
 O <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> método é gerado automaticamente pelo Visual Studio no arquivo de código da faixa de opções. O *ribbonID* parâmetro é uma cadeia de caracteres que identifica o tipo de janela do InfoPath que está sendo aberto.  
  
 O exemplo de código a seguir demonstra como exibir uma faixa de opções personalizada somente em uma janela que exibe um modelo de formulário no modo de design. Especificada na faixa de opções para exibir o `GetResourceText()` método, que é gerado na classe da faixa de opções. Para obter mais informações sobre a classe da faixa de opções, consulte [XML da faixa de opções](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Acessando a faixa de opções em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Designer de faixa de opções](../vsto/ribbon-designer.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)  
  
  