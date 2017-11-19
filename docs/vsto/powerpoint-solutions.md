---
title: "Soluções PowerPoint | Microsoft Docs"
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
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
ms.assetid: 02ebad64-9fd3-495f-ab27-4f6206b3d6d2
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de978f92a5c410312cac00034006cd698b1c5cea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="powerpoint-solutions"></a>Soluções PowerPoint
  O Visual Studio fornece modelos de projeto, que você pode usar para criar suplementos do VSTO para o Microsoft Office PowerPoint. Você pode usar os suplementos do VSTO para automatizar o PowerPoint, estender os recursos do PowerPoint ou personalizar a interface de usuário do PowerPoint (IU).  
  
 Para obter mais informações sobre os suplementos do VSTO, consulte [obtendo iniciado Programando suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md). Se você for novo para programação com o Microsoft Office, consulte [Introdução &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer: criar um suplemento para o Microsoft PowerPoint?](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automating-powerpoint-by-using-the-powerpoint-object-model"></a>Automatizando o PowerPoint usando o modelo de objeto do PowerPoint  
 O modelo de objeto do PowerPoint expõe vários tipos que você pode usar para automatizar o PowerPoint. Esses tipos permitem que você escreva código para realizar tarefas comuns:  
  
-   Criar e formatar apresentações programaticamente.  
  
-   Adicione ou remova a apresentações de slides.  
  
-   Adicionar ou alterar formas em um slide.  
  
 Para acessar o modelo de objeto do PowerPoint de um suplemento do VSTO, use o `Application` campo o `ThisAddIn` classe em seu projeto. O `Application` campo retorna um <xref:Microsoft.Office.Interop.PowerPoint.Application> objeto que representa a instância atual do PowerPoint. Para obter mais informações, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quando você chama o modelo de objeto do PowerPoint, você pode usar tipos fornecidos no assembly de interoperabilidade primário para o PowerPoint. O assembly de interoperabilidade primária atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM no PowerPoint. Todos os tipos no assembly de interoperabilidade primário PowerPoint são definidos no <xref:Microsoft.Office.Interop.PowerPoint> namespace. Para obter mais informações sobre assemblies de interoperabilidade primários, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) e [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a>Usando a documentação de modelo de objeto do PowerPoint  
 Para obter informações completas sobre o modelo de objeto do PowerPoint, você pode consultar para a referência de assembly de interoperabilidade primária (PIA) do PowerPoint e a referência de modelo de objeto VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Referência de Assembly de interoperabilidade primária  
 A documentação de referência do PowerPoint PIA descreve os tipos no assembly de interoperabilidade primário para o PowerPoint. Esta documentação está disponível no seguinte local: [referência de Assembly de interoperabilidade do PowerPoint 2010 primário](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Para obter mais informações sobre o design de PIA do PowerPoint, como as diferenças entre classes e interfaces no PIA e como os eventos em que o PIA são implementados, consulte [visão geral de Classes e Interfaces de Assemblies de interoperabilidade primários do Office ](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>Referência de modelo de objeto do VBA  
 A referência de modelo de objeto VBA documenta o modelo de objeto do PowerPoint como ele é exposto para o Visual Basic para código Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 Todos os objetos e membros na referência de modelo de objeto do VBA correspondem aos tipos e membros na assembly de interoperabilidade primária (PIA) do PowerPoint. Por exemplo, o objeto de apresentação na referência de modelo de objeto do VBA corresponde do <xref:Microsoft.Office.Interop.PowerPoint.Presentation> tipo no PIA do PowerPoint. Embora a referência de modelo de objeto VBA fornece exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA essa referência ao Visual Basic ou Visual c#, se você quiser usá-los em um projeto de suplemento do VSTO do PowerPoint que você cria usando O Visual Studio.  
  
## <a name="customizing-the-user-interface-of-powerpoint"></a>Personalizando a Interface do usuário do PowerPoint  
 Você pode modificar a interface do usuário do PowerPoint das seguintes maneiras.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Crie um painel tarefa personalizada.|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md)|  
|Adicione guias personalizadas para a faixa de opções.|[Visão geral da faixa de opções](../vsto/ribbon-overview.md)|  
|Adicione grupos personalizados a uma guia interna na faixa de opções.|[Como personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Para obter mais informações sobre como personalizar a interface do usuário do PowerPoint e outros aplicativos do Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando seu primeiro suplemento VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Guia de Introdução Programando suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Visão geral sobre o desenvolvimento de soluções do Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  