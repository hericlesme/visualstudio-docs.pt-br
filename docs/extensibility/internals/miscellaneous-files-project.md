---
title: Projeto arquivos diversos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d3fa64b06504d8982594945f5b0c38956676b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="miscellaneous-files-project"></a>Projeto arquivos diversos
Quando um usuário abre itens do projeto, o IDE atribui ao projeto arquivos diversos todos os itens que não são membros de qualquer projetos em uma solução.  
  
 Projetos têm um papel significativo na determinação de qual editor é usado quando um usuário abre um item de projeto. Um projeto pode ser criado para abrir certos arquivos usando um editor específico do projeto ou um editor padrão.  
  
 Um editor específico do projeto normalmente requer que o usuário tem conhecimento especial ou usar interfaces especiais do projeto. Para obter mais informações, consulte [como: editores específicos de projeto abertos](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Um editor padrão pode abrir qualquer arquivo com uma extensão específica em qualquer projeto. O usuário pode personalizar alguns editores padrão, como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seus caracteres pública, mas ainda mantém o editor de texto, para projetos. Editores padrão são criadas usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método.  
  
 Se nenhum projeto na solução responde que ele pode abrir um item de projeto, o IDE oferece um projeto especial chamado projeto arquivos diversos que abre qualquer arquivo.  
  
 Este projeto especial fornece para abertura de um arquivo fora do contexto de um projeto. Durante o processamento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> método, o projeto arquivos diversos sempre responde com uma prioridade muito baixa. Portanto, os arquivos diversos projeto sempre produz a qualquer projeto de prioridade mais alta que possa abrir arquivos.  
  
 O projeto arquivos diversos não exigem que o usuário explicitamente criá-la com a **novo projeto** caixa de diálogo. Além disso, o projeto arquivos diversos não gerencia permanentemente uma lista de membros do projeto. Ele usa um recurso opcional para registrar uma lista de arquivos usados mais recentemente para cada usuário.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)   
 [Adicionando o projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Adicionar modelos projeto e de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)