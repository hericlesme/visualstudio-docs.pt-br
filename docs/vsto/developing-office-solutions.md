---
title: "Desenvolvendo soluções do Office | Microsoft Docs"
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
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
ms.assetid: 7361cfe0-dee4-48d7-a066-232f87f093ca
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 478bd6d27d6e4ef0fe75891d95cdc4b3258a74e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="developing-office-solutions"></a>Desenvolvendo soluções do Office
  Depois que você criar um projeto usando as ferramentas de desenvolvedor do Office no Visual Studio e configurar os arquivos de projeto, você pode começar a se concentrar em implementar o código e a interface do usuário personalizada (UI).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
## <a name="office-solutions-programming-model"></a>Modelo de programação de soluções do Office  
 O modelo de objeto do Office expõe uma variedade de objetos que você pode programar. Sempre que você programar soluções do Office usando código gerenciado, você pode escrever código que usa tipos em assemblies de interoperabilidade primários do Office. Em soluções que você cria usando os modelos de projeto do Office no Visual Studio, você também deve escrever código diretamente em classes geradas em seu projeto. Para obter mais informações, consulte [escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="programming-different-types-of-office-solutions"></a>Programação de diferentes tipos de soluções do Office  
 O tipo de solução que você está criando determina quais recursos você pode usar em seu projeto. Por exemplo, você pode adicionar controles de formulários do Windows e Office estendidos (denominado *hospedar controles*) para personalizações em nível de documento arrastando itens do **caixa de ferramentas** no Visual Studio em tempo de design . No entanto, se você estiver desenvolvendo um suplemento do VSTO, você só pode adicionar esses tipos de controles a documentos em tempo de execução, escrevendo código.  
  
 Para obter mais informações sobre os recursos que são específicas para diferentes tipos de soluções, consulte os tópicos a seguir:  
  
-   [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   [Programando personalizações no nível do documento](../vsto/programming-document-level-customizations.md).  
  
-   [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
 Para obter informações para ajudá-lo a planejar suas soluções do Office e os procedimentos para ajudá-lo a criar projetos, consulte [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)|Descreve os diferentes aspectos de escrever código em soluções do Office.|  
|[Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md)|Fornece uma visão geral do modelo de programação de suplementos do VSTO e tarefas de programação relacionadas.|  
|[Programando personalizações no nível do documento](../vsto/programming-document-level-customizations.md)|Fornece uma visão geral do modelo de programação de tarefas de programação relacionadas e personalizações no nível do documento.|  
|[Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)|Descreve as diferentes maneiras que você pode personalizar os aplicativos de interface do usuário do Office usando os suplementos do VSTO e personalizações no nível do documento.|  
|[Dados em soluções do Office](../vsto/data-in-office-solutions.md)|Descreve as diferentes maneiras que você pode trabalhar com dados em soluções do Office, como associação de dados a controles e cache de dados em personalizações no nível do documento.|  
|[Como o salvamento automático afeta soluções do Office](./how-autosave-impacts-office-solutions.md)|Descreve os ajustes que talvez você precise fazer para soluções do Office ao salvamento automático esteja habilitado.|
|[Solução de problemas de Soluções do Office](../vsto/troubleshooting-office-solutions.md)|Fornece dicas para solucionar problemas comuns que você pode encontrar durante a criação de soluções do Office.|  
|[Suporte a threading no Office](../vsto/threading-support-in-office.md)|Fornece uma visão geral de como trabalhar com vários threads em soluções do Office.|  
|[Acessibilidade em Projetos do Office](../vsto/accessibility-in-office-projects.md)|Descreve os recursos de acessibilidade que estão disponíveis em soluções do Office.|  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar e modificar propriedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Como: ler e gravar em Propriedades do documento](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Como: destinar a Interface de usuário multilíngue do Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Passo a passo: criando o primeiro suplemento do VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Passo a passo: Criando a primeira personalização no nível do documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Passo a passo: Criando seu primeiro suplemento VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Passo a passo: Criando seu primeiro suplemento VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Passo a passo: Criando seu primeiro suplemento VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Passo a passo: Criando seu primeiro suplemento VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Instruções passo a passo: criando a primeira personalização no nível de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  