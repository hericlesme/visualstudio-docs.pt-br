---
title: Prioridade do projeto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ae692249ea952970b096825c8f6968158eb2f17f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="project-priority"></a>Prioridade do projeto
Geralmente, um item de projeto é um membro de apenas um projeto na solução. Portanto, o IDE pode facilmente determinar qual projeto é usado para abrir o item. No entanto, se um item for um membro de mais de um projeto, o IDE usa um esquema de prioridade para determinar o melhor projeto para abrir o item.  
  
 A lista a seguir mostra o esquema de prioridades de projeto:  
  
-   O IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> método para cada projeto na solução para determinar se o documento é um membro desse projeto.  
  
-   Se o documento é um membro do projeto, o projeto responde com uma prioridade que o projeto atribui acordo com a manipulação do documento. Por exemplo, um projeto de linguagem responde com uma prioridade alta para arquivos de origem de idioma, mas responde com uma prioridade mais baixa para um tipo de arquivo não reconhecido que não é usado como parte de seu processo de compilação.  
  
-   Os projetos que fornecem designers ou editores personalizados, específicos do projeto para um documento também recebem uma prioridade alta.  
  
-   O <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeração fornece o documento de valores de prioridade.  
  
-   O projeto que especifica a prioridade mais alta recebe o contexto para abrir o documento. Se dois projetos retornam valores de prioridade igual, o projeto ativo é preferencial. Se nenhum projeto na solução responde que ele pode abrir o documento, o IDE coloca o documento no projeto arquivos diversos. Para obter mais informações, consulte [projeto arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Consulte também  
 [Projeto arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md)   
 [Como: abrir editores para documentos abertos](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Adicionar modelos projeto e de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)