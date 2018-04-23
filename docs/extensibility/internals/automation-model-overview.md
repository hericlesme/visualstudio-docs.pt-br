---
title: Visão geral do modelo de automação | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9369bb6074bb294223051ba7dfa158648fe0cad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="automation-model-overview"></a>Visão geral do modelo de automação
O modelo de automação consiste em um conjunto de objetos em relação ao qual você pode escrever um suplemento do Visual Studio ou a extensão. Um suplemento é um aplicativo que pode manipular o ambiente do Visual Studio e automatizar tarefas comuns. Uma extensão do Visual Studio pode criar componentes personalizados do Visual Studio ou adicionar a funcionalidade dos componentes padrão, como o editor de texto.  
  
## <a name="objects-in-the-automation-model"></a>Objetos do modelo de automação  
 O modelo de automação consiste em grupos de objetos que controlam os principais aspectos do ambiente comum. Este é um diagrama que mostra o amplo conjunto de objetos que compõem o modelo de automação.  
  
 ![Gráfico de objetos de automação do Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Objetos de automação do Visual Studio  
  
 Para obter mais informações, consulte [estendendo o ambiente do Visual Studio](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 O ambiente fornece um modelo para diferentes áreas funcionais. Por exemplo, há um modelo de código para vários elementos que você pode encontrar no código. Há um modelo de documento para vários elementos de documento. Uma área, área de projeto, é de particular interesse VSPackage provedores. Provavelmente você desejará seus novos tipos de projeto contribuir para o modelo de automação da mesma maneira como [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuem para o modelo de automação. Se o processo é descrito na [fornecendo automação para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Locais onde você pode considerar estendendo o modelo de automação do ambiente:  
  
-   Projeto  
  
-   Documento  
  
-   Código  
  
-   Build  
  
 Para obter mais informações sobre a automação, consulte [automação e extensibilidade do Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Este documento e os documentos que ela fornece links para ajudá-lo a tomar decisões sobre como você deve fornecer a automação para o VSPackage.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar um suplemento](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)