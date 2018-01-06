---
title: "Soluções InfoPath | Microsoft Docs"
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
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
ms.assetid: 20ac6bee-b17f-4217-9f78-11304a11236a
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: da9cebf8d4c8a30821585160ff07edd6eae0cd7c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="infopath-solutions"></a>Soluções InfoPath
  O Visual Studio fornece modelos de projeto, que você pode usar para criar suplementos do VSTO para o Microsoft Office InfoPath 2013 e InfoPath 2010. O InfoPath não está disponível no Office 2016.  
  
> [!NOTE]  
>  Você ainda pode criar um suplemento do VSTO para InfoPath mesmo se você tiver instalado o Office 2016. Instale apenas o InfoPath 2013 ou Office 2013-lado a lado com o Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
 Suplementos do VSTO para InfoPath são semelhantes ao suplemento do VSTO para outros aplicativos do Microsoft Office. Esses tipos de soluções consistem em um assembly que é carregado pelo aplicativo. Os usuários finais podem ter acesso à funcionalidade desse assembly não importa qual formulário ou modelo é aberto. Para obter mais informações sobre os suplementos do VSTO, consulte [obtendo iniciado Programando suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 não inclui os projetos de modelo de formulário do InfoPath que foram fornecidos nas versões anteriores do Visual Studio. Você também não pode usar o Visual Studio 2015 para abrir ou editar um projeto de modelo de formulário do InfoPath foi criado em uma versão anterior do Visual Studio. No entanto, você pode abrir e editar um projeto de modelo de formulário do InfoPath usando Visual Studio Tools for Applications. Para obter mais informações, consulte [trabalhar com projetos de 2008 do VSTO em InfoPath 2010.](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## <a name="automating-infopath-by-using-an-add-in"></a>Automatizando o InfoPath usando um suplemento  
 Para acessar o modelo de objeto do InfoPath do Office VSTO e suplementos criados usando ferramentas de desenvolvimento do Office no Visual Studio, use o `Application` campo o `ThisAddIn` classe em seu projeto. O `Application` campo retorna um <xref:Microsoft.Office.Interop.InfoPath.Application> objeto que representa a instância atual do InfoPath. Para obter mais informações, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quando você chama o modelo do objeto do InfoPath de um suplemento do VSTO, você pode usar tipos fornecidos no assembly de interoperabilidade primário para InfoPath. O assembly de interoperabilidade primária atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM do InfoPath. Todos os tipos no assembly de interoperabilidade primário do InfoPath são definidos no <xref:Microsoft.Office.Interop.InfoPath> namespace. Para obter mais informações sobre o assembly de interoperabilidade primária do InfoPath, consulte [sobre o Microsoft Office InfoPath Assembly de interoperabilidade primário](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Para obter mais informações sobre assemblies de interoperabilidade primários em geral, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) e [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="customizing-the-user-interface-of-infopath-by-using-an-add-in"></a>Personalizando a Interface do usuário do InfoPath usando um suplemento  
 Quando você criar um suplemento do VSTO para InfoPath, você tem várias opções diferentes de personalização da interface do usuário. A tabela a seguir lista algumas dessas opções.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Crie um painel tarefa personalizada.|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md)|  
|Adicione guias personalizadas para a faixa de opções do InfoPath.|[Personalizando uma faixa de opções para InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Para obter mais informações sobre como personalizar a interface do usuário do InfoPath e outros aplicativos do Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Sobre o Assembly de interoperabilidade primária do InfoPath do Microsoft Office](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Guia de Introdução Programando suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Visão geral sobre o desenvolvimento de soluções do Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [InfoPath 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  