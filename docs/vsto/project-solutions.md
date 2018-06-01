---
title: Soluções de projeto
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3364c778b8dfc290ef06b7daa5ba063ac31f3db
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692594"
---
# <a name="project-solutions"></a>Soluções de projeto
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fornece modelos de projeto, que você pode usar para criar suplementos do VSTO para o Microsoft Office Project. Você pode usar os suplementos do VSTO para automatizar o projeto, estender os recursos de projeto ou personalizar a interface de usuário (IU) do Project.  
  
 Para obter mais informações sobre os suplementos do VSTO, consulte [começar a programar suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md). Se você for novo para programação com o Microsoft Office, consulte [começar &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
## <a name="automate-project-by-using-the-project-object-model"></a>Automatizar o projeto usando o modelo de objeto do projeto  
 O modelo de objeto do projeto expõe vários tipos que você pode usar para automatizar o projeto. Esses tipos permitem que você escreva código para realizar tarefas comuns como programaticamente criando e modificando tarefas em um projeto.  
  
 Para acessar o modelo de objeto do projeto de um suplemento do VSTO, use o `Application` campo o `ThisAddIn` classe em seu projeto. O `Application` campo retorna um `Microsoft.Office.Interop.MsProject.Application` objeto que representa a instância atual do projeto. Para obter mais informações, consulte [suplementos do VSTO do programa](../vsto/programming-vsto-add-ins.md).  
  
 Quando você chama o modelo de objeto do projeto, você pode usar tipos fornecidos no assembly de interoperabilidade primário para o projeto. O assembly de interoperabilidade primária atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM do projeto. Todos os tipos no assembly de interoperabilidade primária do projeto são definidos no `Microsoft.Office.Interop.MSProject` namespace. Para obter mais informações sobre assemblies de interoperabilidade primários, consulte [visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) e [assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="use-the-project-object-model-documentation"></a>Use a documentação de modelo de objeto do projeto  
 Para obter informações completas sobre o modelo de objeto do projeto, consulte a referência de modelo de objeto de projeto VBA. A referência de modelo de objeto VBA documenta o modelo de objeto do projeto como ele é exposto para o Visual Basic para código Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Todos os objetos e membros na referência de modelo de objeto do VBA correspondem aos tipos e membros na assembly de interoperabilidade primário (PIA) do projeto. Por exemplo, o objeto de calendário na referência de modelo de objeto do VBA corresponde do `Microsoft.Office.Interop.MSProject.Calendar` tipo no PIA do projeto. Embora a referência de modelo de objeto VBA fornece exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA essa referência ao Visual Basic ou Visual c#, se você quiser usá-los em um projeto de suplemento do VSTO de projeto que você cria usando O Visual Studio.  
  
> [!NOTE]  
>  Neste momento, não há nenhuma documentação de referência para o assembly de interoperabilidade primária do projeto.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Tipos de infraestrutura no assembly de interoperabilidade primária do projeto  
 Como escrever um código que usa o PIA do projeto, você poderá notar muitos tipos que não são descritos na referência do VBA. Esses tipos adicionais ajuda converta os objetos no modelo de objeto baseado em COM do projeto para código gerenciado, não se destina a ser usado diretamente no seu código.  
  
 Para obter mais informações, consulte [visão geral de classes e interfaces de assemblies de interoperabilidade primários do Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customize-the-user-interface-of-project"></a>Personalizar a interface do usuário do projeto  
 Você pode personalizar a interface do usuário do projeto das seguintes maneiras.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Adicionar guias personalizadas para a faixa de opções no projeto|[Visão geral da faixa de opções](../vsto/ribbon-overview.md)|  
  
 Para obter mais informações sobre como personalizar a interface do usuário do projeto e outros aplicativos do Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criar o primeiro VSTO Add-in do projeto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Visão geral sobre o desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programa de suplementos do VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Project 2010 e do Project Server 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  