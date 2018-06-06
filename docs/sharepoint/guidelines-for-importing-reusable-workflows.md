---
title: Diretrizes para importar fluxos de trabalho reutilizáveis | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e88a8549700158a677b019424df5736cb9cc3a55
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767313"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Diretrizes para importar fluxos de trabalho reutilizáveis
  Para importar fluxos de trabalho reutilizáveis criados no SharePoint Designer, use o modelo de projeto importar do SharePoint 2010 fluxo de trabalho reutilizável no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Este modelo importa um *declarativa* *fluxo de trabalho* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-somente) e o converte em um *código de fluxo de trabalho*, que é um fluxo de trabalho que você pode aprimorar com um [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] código. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Passo a passo: Importar um fluxo de trabalho reutilizável do Designer do SharePoint no Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 No entanto, o modelo de importação do SharePoint 2010 fluxo de trabalho reutilizável pode importar apenas soluções de farm. Se você quiser implantar seu fluxo de trabalho como uma solução em área restrita, importá-lo com o modelo de importar pacote de solução do SharePoint 2010. No entanto, ao fazer isso, não é possível convertê-lo para codificar o fluxo de trabalho e não será possível modificá-lo como tal.  
  
## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importar fluxos de trabalho reutilizáveis usando o modelo de importação de fluxo de trabalho reutilizável
 Se você importar um fluxo de trabalho reutilizável, usando o modelo de importação do SharePoint 2010 fluxo de trabalho reutilizável, você pode executar ou alterar a solução como qualquer outro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solução do SharePoint, mas você talvez precise corrigir manualmente alguns itens.  
  
### <a name="import-task-forms"></a>Importar formulários de tarefa
 O modelo de projeto de fluxo de trabalho do importação reutilizável do SharePoint 2010 importa todos os formulários de iniciação e de associação, mas importa o formulário de apenas uma tarefa porque o esquema do fluxo de trabalho de código só permite que um formulário de tarefa. Todos os formulários tarefas adicionais de solução de fluxo de trabalho original são colocados no **outros arquivos importados** pasta **Gerenciador de soluções**.  
  
## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importar fluxos de trabalho reutilizáveis usando o modelo de importar pacote de solução do SharePoint 2010
 Se você importar um fluxo de trabalho reutilizável, usando o modelo de importar pacote de solução do SharePoint 2010, você precisa considerar os seguintes problemas:  
  
-   Depois de importar o fluxo de trabalho, você pode imediatamente implantar e executá-lo no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] escolhendo o **F5** chave. No entanto, se você alterar qualquer coisa no fluxo de trabalho na solução importada, você precisará corrigir manualmente os elementos no projeto antes de implantar e executar o fluxo de trabalho.  
  
-   Como o fluxo de trabalho declarativo, o código não pode ser adicionado a ele. Para converter o fluxo de trabalho em um fluxo de trabalho de código, você deve importá-lo para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando o modelo de importação do SharePoint 2010 fluxo de trabalho reutilizável.  
  
-   Enquanto você pode editar o arquivo de designer (. xoml) de fluxo de trabalho no modo de Design, é recomendável editá-lo no modo de exibição de fonte, como o designer de fluxo de trabalho exibe erros falsos.  
  
-   Depuração no fluxo de trabalho não funciona para o conteúdo declarativo. Pontos de interrupção definidos [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] não serão ativados.  
  
## <a name="import-globally-reusable-workflow-solutions"></a>Soluções de fluxo de trabalho reutilizável globalmente de importação
 Fluxos de trabalho reutilizáveis global não podem ser importados usando o modelo de importação do SharePoint 2010 fluxo de trabalho reutilizável. Para importar um fluxo de trabalho reutilizável globalmente, você precisa convertê-la em um fluxo de trabalho reutilizável não globalmente ou você deve usar o modelo de importar pacote de solução do SharePoint 2010.  
  
 Para converter o fluxo de trabalho, faça uma cópia do fluxo de trabalho reutilizável globalmente no SharePoint Designer (abrindo o menu de atalho para o fluxo de trabalho e, em seguida, escolhendo **Salvar como cópia**). Em seguida, importe o novo fluxo de trabalho reutilizável com o modelo de importação do SharePoint 2010 fluxo de trabalho reutilizável no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Para importar o fluxo de trabalho reutilizável globalmente sem modificá-lo, use o modelo de importar pacote de solução do SharePoint 2010. Se você usar esse método, o fluxo de trabalho não é convertido em um fluxo de trabalho de código e permanece um fluxo de trabalho declarativo.  
  
## <a name="see-also"></a>Consulte também
 [Importando itens de um Site do SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Instruções passo a passo: importar um fluxo de trabalho reutilizável do designer do SharePoint para o Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  
