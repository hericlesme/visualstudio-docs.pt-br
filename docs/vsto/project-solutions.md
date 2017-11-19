---
title: "Soluções de projeto | Microsoft Docs"
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
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 584f98e9fbe6a8883039cad03e6b0782d225b8bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="project-solutions"></a>Soluções do projeto
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]fornece modelos de projeto, que você pode usar para criar suplementos do VSTO para o Microsoft Office Project. Você pode usar os suplementos do VSTO para automatizar o projeto, estender os recursos de projeto ou personalizar a interface de usuário (IU) do Project.  
  
 Para obter mais informações sobre os suplementos do VSTO, consulte [obtendo iniciado Programando suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md). Se você for novo para programação com o Microsoft Office, consulte [Introdução &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
## <a name="automating-project-by-using-the-project-object-model"></a>Automatizando o projeto usando o modelo de objeto do projeto  
 O modelo de objeto do projeto expõe vários tipos que você pode usar para automatizar o projeto. Esses tipos permitem que você escreva código para realizar tarefas comuns como programaticamente criando e modificando tarefas em um projeto.  
  
 Para acessar o modelo de objeto do projeto de um suplemento do VSTO, use o `Application` campo o `ThisAddIn` classe em seu projeto. O `Application` campo retorna um objeto Microsoft.Office.Interop.MsProject.Application que representa a instância atual do projeto. Para obter mais informações, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quando você chama o modelo de objeto do projeto, você pode usar tipos fornecidos no assembly de interoperabilidade primário para o projeto. O assembly de interoperabilidade primária atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM do projeto. Todos os tipos no assembly de interoperabilidade primária do projeto são definidos no namespace Microsoft.Office.Interop.MSProject. Para obter mais informações sobre assemblies de interoperabilidade primários, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) e [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="using-the-project-object-model-documentation"></a>Usando a documentação de modelo de objeto do projeto  
 Para obter informações completas sobre o modelo de objeto do projeto, consulte a referência de modelo de objeto de projeto VBA. A referência de modelo de objeto VBA documenta o modelo de objeto do projeto como ele é exposto para o Visual Basic para código Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do projeto 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Todos os objetos e membros na referência de modelo de objeto do VBA correspondem aos tipos e membros na assembly de interoperabilidade primário (PIA) do projeto. Por exemplo, o objeto de calendário na referência de modelo de objeto do VBA corresponde ao tipo de Microsoft.Office.Interop.MSProject.Calendar no PIA do projeto. Embora a referência de modelo de objeto VBA fornece exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA essa referência ao Visual Basic ou Visual c#, se você quiser usá-los em um projeto de suplemento do VSTO de projeto que você cria usando O Visual Studio.  
  
> [!NOTE]  
>  Neste momento, não há nenhuma documentação de referência para o assembly de interoperabilidade primária do projeto.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Tipos de infraestrutura no Assembly de interoperabilidade primária do projeto  
 Como escrever um código que usa o PIA do projeto, você poderá notar muitos tipos que não são descritos na referência do VBA. Esses tipos adicionais ajuda converta os objetos no modelo de objeto baseado em COM do projeto para código gerenciado, não se destina a ser usado diretamente no seu código.  
  
 Para obter mais informações, consulte[visão geral de Classes e Interfaces de Assemblies de interoperabilidade primários do Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customizing-the-user-interface-of-project"></a>Personalizando a Interface do usuário do projeto  
 Você pode personalizar a interface do usuário do projeto das seguintes maneiras.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Adicionar guias personalizadas para a faixa de opções no projeto|[Visão geral da faixa de opções](../vsto/ribbon-overview.md)|  
  
 Para obter mais informações sobre como personalizar a interface do usuário do projeto e outros aplicativos do Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando seu primeiro suplemento VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Guia de Introdução Programando suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Visão geral sobre o desenvolvimento de soluções do Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Project 2010 e do Project Server 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  