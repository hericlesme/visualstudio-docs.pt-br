---
title: 'Como: usar o gerenciamento de desfazer vinculado | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a025cdfc14eb39dad7ea2bc72a69f1f260fb583
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-linked-undo-management"></a>Como: usar o gerenciamento de desfazer vinculado
Desfazer vinculado permite ao usuário desfazer simultaneamente as mesmo edições em vários arquivos. Por exemplo, as alterações no texto simultâneas em vários arquivos de programa, como um arquivo de cabeçalho e um arquivo de Visual C++, é uma transação desfazer vinculado. Capacidade de desfazer vinculado está incorporada a implementação do ambiente do Gerenciador de desfazer, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> permite manipular esse recurso. Desfazer vinculado é implementado por uma unidade para desfazer pai que pode vincular pilhas de desfazer separado para ser tratado como uma unidade única de desfazer. O procedimento para usar desfazer vinculado é detalhado na seção a seguir.  
  
### <a name="to-use-linked-undo"></a>Para usar um Desfazer vinculado  
  
1.  Chamar `QueryService` na `SVsLinkedUndoManager` para obter um ponteiro para `IVsLinkedUndoTransactionManager`.  
  
2.  Criar uma unidade de desfazer vinculado pai inicial chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Isso define o ponto de partida para um conjunto de pilhas de desfazer sejam agrupados em pilhas de desfazer vinculado. No `OpenLinkedUndo` método, você também precisará especificar se deseja que o desfazer vinculado não estrito ou strict. Desfazer vinculado não estrito comportamento significa que alguns dos documentos com irmãos de desfazer vinculado podem fechar e ainda deixar o outro vinculado desfazer irmãos em suas pilhas. Comportamento de desfazer vinculado estrito Especifica que todas as pilhas de irmão de desfazer vinculado precisam ser desfeita juntos ou nenhum. Adicionar subsequentes vinculado desfazer pilhas chamando [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) método.  
  
3.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> para reverter todas as unidades de desfazer vinculado como um.  
  
    > [!NOTE]
    >  Para implementar o gerenciamento de desfazer vinculado em um editor, adicione o gerenciamento de desfazer. Para obter mais informações sobre como implementar o gerenciamento de desfazer vinculado, consulte [como: implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Como: implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)