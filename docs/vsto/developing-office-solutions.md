---
title: Desenvolver soluções do Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd5829a3d09d96ad0ed9cfce3dd4bc329e70f907
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="develop-office-solutions"></a>Desenvolver soluções do Office
  Depois que você criar um projeto usando as ferramentas de desenvolvedor do Office no Visual Studio e configurar os arquivos de projeto, você pode começar a se concentrar em implementar o código e a interface do usuário personalizada (UI).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
## <a name="office-solutions-programming-model"></a>Modelo de programação de soluções do Office  
 O modelo de objeto do Office expõe uma variedade de objetos que você pode programar. Sempre que você programar soluções do Office usando código gerenciado, você pode escrever código que usa tipos em assemblies de interoperabilidade primários do Office. Em soluções que você cria usando os modelos de projeto do Office no Visual Studio, você também deve escrever código diretamente em classes geradas em seu projeto. Para obter mais informações, consulte [escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="program-different-types-of-office-solutions"></a>Tipos diferentes de programa de soluções do Office  
 O tipo de solução que você está criando determina quais recursos você pode usar em seu projeto. Por exemplo, você pode adicionar controles de formulários do Windows e Office estendidos (denominado *hospedar controles*) para personalizações em nível de documento arrastando itens do **caixa de ferramentas** no Visual Studio em tempo de design . No entanto, se você estiver desenvolvendo um suplemento do VSTO, você só pode adicionar esses tipos de controles a documentos em tempo de execução, escrevendo código.  
  
 Para obter mais informações sobre os recursos que são específicas para diferentes tipos de soluções, consulte os tópicos a seguir:  
  
-   [Programa de suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   [Personalizações no nível do documento de programa](../vsto/programming-document-level-customizations.md).  
  
-   [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
 Para obter informações para ajudá-lo a planejar suas soluções do Office e os procedimentos para ajudá-lo a criar projetos, consulte [Design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)|Descreve os diferentes aspectos de escrever código em soluções do Office.|  
|[Programa de suplementos do VSTO](../vsto/programming-vsto-add-ins.md)|Fornece uma visão geral do modelo de programação de suplementos do VSTO e tarefas de programação relacionadas.|  
|[Programa personalizações no nível do documento](../vsto/programming-document-level-customizations.md)|Fornece uma visão geral do modelo de programação de tarefas de programação relacionadas e personalizações no nível do documento.|  
|[Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)|Descreve as diferentes maneiras que você pode personalizar os aplicativos de interface do usuário do Office usando os suplementos do VSTO e personalizações no nível do documento.|  
|[Dados em soluções do Office](../vsto/data-in-office-solutions.md)|Descreve as diferentes maneiras que você pode trabalhar com dados em soluções do Office, como associação de dados a controles e cache de dados em personalizações no nível do documento.|  
|[Como o salvamento automático afeta soluções do Office](./how-autosave-impacts-office-solutions.md)|Descreve os ajustes que talvez você precise fazer para soluções do Office ao salvamento automático esteja habilitado.|
|[Solucionar problemas de soluções do Office](../vsto/troubleshooting-office-solutions.md)|Fornece dicas para solucionar problemas comuns que você pode encontrar durante a criação de soluções do Office.|  
|[Suporte a Threading no Office](../vsto/threading-support-in-office.md)|Fornece uma visão geral de como trabalhar com vários threads em soluções do Office.|  
|[Acessibilidade em projetos do Office](../vsto/accessibility-in-office-projects.md)|Descreve os recursos de acessibilidade que estão disponíveis em soluções do Office.|  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar e modificar propriedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Como: ler e gravar propriedades de documento](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Como: destinar a interface de usuário multilíngue do Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Passo a passo: Criar seu primeiro VSTO suplemento para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Passo a passo: Criar a primeira personalização no nível do documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Passo a passo: Criar seu primeiro VSTO suplemento para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Passo a passo: Criar o primeiro Add-in do VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Passo a passo: Criar o primeiro VSTO Add-in do projeto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Passo a passo: Criar o primeiro Add-in do VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Passo a passo: Criar a primeira personalização no nível do documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  