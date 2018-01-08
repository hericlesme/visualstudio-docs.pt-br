---
title: "Suporte a formulários em fluxos de trabalho | Microsoft Docs"
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
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0da90955a590881a02117213246e580339dbe596
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="form-support-in-workflows"></a>Suporte de formulário em fluxos de trabalho
  Quatro tipos de formulários podem ser usados em um fluxo de trabalho: associação, inicialização, tarefa e modificação. Esses tipos de formulário podem ser baseados em um formulário ASPX ou um formulário do InfoPath. O nível de suporte que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornece para um formulário específico depende de vários fatores, que são descritos nas tabelas a seguir. Para obter mais informações sobre os tipos de formulário de fluxo de trabalho, consulte [visão geral de formulários de fluxo de trabalho](http://go.microsoft.com/fwlink/?LinkId=185228) no site do MSDN.  
  
## <a name="xml-refactoring"></a>Refatoração de XML  
 Quando você adiciona um formulário de associação ou o início de ASPX para um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] item de projeto de fluxo de trabalho, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automaticamente refatora o XML no arquivo Elements XML do fluxo de trabalho para manter o atributo que se refere ao formulário de associação ou o início sincronizado sempre que o caminho de implantação ou o nome do formulário é atualizado ou o formulário é excluído. No entanto, quando você usar outros tipos de formulário em um fluxo de trabalho, como um formulário de tarefa ou modificação, o arquivo Elements não é refatorado.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Suporte de formulário em novos fluxos de trabalho do Visual Studio  
 A seguinte tabela lista [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] suporte para tipos de forma diferente em formulários ASPX ou InfoPath em fluxos de trabalho que são criados no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo de formulário|Fluxo de trabalho criado no Visual Studio com um formulário ASPX|Fluxo de trabalho criado no Visual Studio usando um formulário do InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Associação|-Um formulário de associação ASPX pode ser adicionado ao fluxo de trabalho usando o **formulário de associação de fluxo de trabalho** modelo de item.<br />-Quando o formulário é adicionado, renomeado ou excluído, ou quando altera seu caminho de implantação, é refatorado o arquivo Elements do fluxo de trabalho.<br />-Para obter mais informações, consulte [passo a passo: Criando um fluxo de trabalho com associação e formulários de iniciação](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Não há nenhum modelo de formulário de associação do InfoPath em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Não há nenhuma integração entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e o Designer do InfoPath.<br />-O arquivo Elements do fluxo de trabalho não é refatorado.|  
|Iniciação|-Um formulário de iniciação ASPX pode ser adicionado ao fluxo de trabalho usando o **formulário de iniciação do fluxo de trabalho** modelo de item.<br />-Quando o formulário é adicionado, renomeado ou excluído, ou quando altera seu caminho de implantação, é refatorado o arquivo Elements do fluxo de trabalho.<br />-Para obter mais informações, consulte [passo a passo: Criando um fluxo de trabalho com associação e formulários de iniciação](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Não há nenhum modelo de formulário de associação do InfoPath em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Não há nenhuma integração entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e o Designer do InfoPath.<br />-O arquivo Elements do fluxo de trabalho não é refatorado.|  
|Tarefa|-Nenhum modelo de formulário de tarefa ASPX está disponível em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Você deve criar uma página de aplicativo e adicione o código a ele.<br />-O arquivo Elements do fluxo de trabalho não é refatorado.<br />-Para obter mais informações, consulte [formulários de tarefa de fluxo de trabalho (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-Não há nenhum modelo de formulário de tarefa do InfoPath em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Não há nenhuma integração entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e o Designer do InfoPath.<br />-O arquivo Elements do fluxo de trabalho não é refatorado.|  
|Modificação|-Nenhum modelo de formulário de modificação ASPX está disponível em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para adicionar um formulário de modificação, você deve criar uma página de aplicativo e adicione o código a ele.<br />-O arquivo Elements do fluxo de trabalho não é refatorado. Você deve editar manualmente-lo conforme apropriado.<br />-Para obter mais informações, consulte [formulários de modificação de fluxo de trabalho (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-Não há nenhum modelo de formulário do InfoPath modificação em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Não há nenhuma integração entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e o Designer do InfoPath.<br />-O arquivo Elements do fluxo de trabalho não é refatorado.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Suporte de formulário em fluxos de trabalho reutilizáveis importado do SharePoint  
 A seguinte tabela lista [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] suporte para tipos de forma diferente em formulários ASPX ou InfoPath em fluxos de trabalho reutilizáveis do SharePoint que são importados para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo de formulário|Fluxo de trabalho reutilizável que tenha um formulário ASPX importado do SharePoint Designer|Fluxo de trabalho reutilizável que tenha um formulário do InfoPath importado do SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Associação|-O formulário é referenciado no arquivo Elements do fluxo de trabalho.<br />-Quando o formulário for renomeado ou excluído, ou quando altera seu caminho de implantação, é refatorado o arquivo Elements do fluxo de trabalho.|-O formulário é importado, mas não é referenciado em Elements do fluxo de trabalho.<br />-O arquivo Elements do fluxo de trabalho não é refatorado.|  
|Iniciação|-O formulário é referenciado pelo fluxo de trabalho no arquivo Elements do fluxo de trabalho.<br />-Quando o formulário for renomeado ou excluído, ou quando altera seu caminho de implantação, é refatorado o arquivo Elements do fluxo de trabalho.|-O formulário é importado, mas não é referenciado em Elements do fluxo de trabalho.<br />-O arquivo Elements do fluxo de trabalho não é refatorado. **Observação:** regras e propriedades devem ser adicionadas e alteradas para este cenário funcione.|  
|Tarefa|-O formulário é referenciado no arquivo Elements do fluxo de trabalho.<br />-O arquivo Elements do fluxo de trabalho não é refatorado.|-O formulário é importado, mas não é referenciado em Elements do fluxo de trabalho.<br />-O arquivo Elements do fluxo de trabalho não é refatorado. **Observação:** regras e propriedades devem ser adicionadas e alteradas para este cenário funcione.|  
|Modificação|Não aplicável. Não não possível criar formulários de modificação ASPX no SharePoint Designer.|Não aplicável. Formulários de modificação do InfoPath não não possível criar no SharePoint Designer, exceto para o fluxo de trabalho de servidor do SharePoint interno, que não está incluído no arquivo. wsp quando o fluxo de trabalho é exportado.|  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um fluxo de trabalho com associação e formulários de iniciação](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Criação de soluções de fluxo de trabalho do SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importando itens de um site existente do SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  