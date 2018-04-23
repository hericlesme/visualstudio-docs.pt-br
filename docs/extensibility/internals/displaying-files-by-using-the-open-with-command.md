---
title: Exibindo arquivos usando a abrir com o comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9c708bb5a510748b08cac5b46b6829b908e74e0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Exibindo arquivos usando a abrir com o comando
Um projeto pode solicitar o IDE para exibir o **abrir com** caixa de diálogo. Essa solicitação solicita ao usuário para abrir um arquivo que tenha uma seleção de editores padrão. As etapas a seguir descrevem esse processo.  
  
1.  As chamadas de projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, especificando um valor de OSE_UseOpenWithDialog para o `OSEOpenDocEditor` parâmetro.  
  
2.  Com base na extensão de nome de arquivo do documento, o IDE determina quais editores listados no podem registro abram o documento especificado e exibe essas informações no **abrir com** caixa de diálogo.  
  
    > [!NOTE]
    >  Projetos com um editor intrínseco que deve ser incluído no **abrir com** caixa de diálogo deve registrar uma fábrica de editor para cada editor tal. Editores intrínsecos funcionam apenas junto com um determinado tipo de projeto, que é imposto na implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método. O IDE tem uma fábrica de editor interno para o editor de texto principal e o editor binário. O IDE também cria uma instância de uma fábrica de editor em nome de cada associação de arquivo registrada do Windows. Um exemplo desse tipo de arquivo é o Microsoft Word.  
  
3.  Assim que o usuário seleciona um item a partir de **abrir com** caixa de diálogo, em seguida, o IDE abre o documento chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método. Para obter mais informações, consulte [como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Consulte também  
 [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Exibindo arquivos usando o comando Abrir arquivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Como abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)