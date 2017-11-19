---
title: "Gerenciamento de proprietário de bloqueio de documentos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4bd487bd3f5a6978af9f79eb9e0a00866b5df52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="document-lock-holder-management"></a>Gerenciamento de proprietário de bloqueio de documentos
A tabela de documento em execução (RDT) mantém uma contagem de documentos abertos e todos eles têm os bloqueios de edição. Você pode colocar um bloqueio de edição em um documento de RDT quando ele é editado por meio de programação em segundo plano sem que o usuário ver um documento aberto em uma janela de documento. Essa funcionalidade é frequentemente usada pelos designers que modificar vários arquivos por meio de uma interface gráfica do usuário.  
  
## <a name="document-lock-holder-scenarios"></a>Cenários de proprietário de bloqueio de documento  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Arquivo "a" uma dependência no arquivo tem "b"  
 Considere uma situação em que você implementar um editor padrão "A" para o tipo de arquivo "a" e cada arquivo do tipo "um" tem uma referência a (ou a dependência de) um arquivo do tipo "b". Existe um editor padrão "B" para arquivos do tipo "b". Quando o editor de "A" abre o arquivo "r" recupera a referência ao arquivo correspondente "b". O arquivo "b" não é exibido, mas editor "A" poderá modificá-lo. Editor de "A" obtém uma referência aos dados de documento do arquivo de "b" do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método e também mantém um bloqueio de edição no arquivo "b". Após a conclusão do editor de "A" modificando o arquivo "b", você pode diminuir o bloqueio de edição contagem no arquivo "b", chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> método. Você pode omitir essa etapa se você tivesse chamado o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método com o parâmetro `dwRDTLockType` definido como <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>O arquivo "b" é aberto por um outro Editor  
 Se o arquivo "b" já está aberto por editor "B" quando o editor de "A" tenta abri-lo, há dois cenários separados para lidar com:  
  
-   Se o arquivo "b" está aberto em um editor compatível, você deve ter editor "A" registrar um bloqueio de edição do documento no arquivo "b" usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> método. Após seu editor "A" Modificar arquivo "b", cancele o registro do documento editar bloqueio usando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> método.  
  
-   Se o arquivo "b" está aberto em um modo incompatível, você pode deixar que a tentativa abertura de arquivo "b" por "A" falha, ou você pode deixar a exibição associada com o editor de "A" parcialmente aberto e exibirá uma mensagem de erro apropriado de editor. A mensagem de erro deve instruir o usuário fechar o arquivo "b" no editor incompatível e abra novamente o arquivo "a" usando o editor de "A". Você também pode implementar o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> para solicitar ao usuário para fechar o arquivo "b" é aberto no editor incompatível. Se o usuário fecha o arquivo "b", a abertura do arquivo de "a" no editor "A" continuará normalmente.  
  
## <a name="additional-document-edit-lock-considerations"></a>Considerações de bloqueio de editar documentos adicionais  
 Você receberá um comportamento diferente se o editor "A" é o único editor que tem um documento de editar o bloqueio no arquivo "b" do que o editor "B" também contém um documento editar bloqueio no arquivo "b". Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Designer de classe** é um exemplo de um designer visual que não possui um bloqueio de editar o arquivo de código associado. Ou seja, se o usuário tem um diagrama de classe aberto no modo de design e o arquivo de código associado abertos simultaneamente, e se o usuário modifica o arquivo de código, mas não salvar as alterações, as alterações também serão perdidas ao arquivo de diagrama (.cd) de classe. Se o **Designer de classe** tem o documento somente editar bloqueio no arquivo de código, o usuário não é solicitado a salvar as alterações ao fechar o arquivo de código. O IDE pede ao usuário para salvar as alterações somente depois que o usuário fecha o **Designer de classe**. Salvar alterações são refletidas em ambos os arquivos. Se o **Designer de classe** e o editor de arquivo de código mantidos bloqueios de edição do documento no arquivo de código, em seguida, o usuário é solicitado a salvar ao fechar o arquivo de código ou o formulário. Nesse ponto, as alterações salvas são refletidas no formulário e o arquivo de código. Para obter mais informações sobre diagramas de classe, consulte [trabalhando com diagramas de classe (Designer de classe)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Observe que se você precisa colocar um bloqueio de edição em um documento para um editor não, você deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface.  
  
 Muitas vezes um interface do usuário designer que modifica os arquivos de código por meio de programação faz alterações em mais de um arquivo. Nesses casos o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> método manipula o salvamento de um ou mais documentos por meio do **você deseja salvar as alterações nos itens a seguir?** caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de documento em execução](../extensibility/internals/running-document-table.md)   
 [Persistência e tabela de documento em execução](../extensibility/internals/persistence-and-the-running-document-table.md)