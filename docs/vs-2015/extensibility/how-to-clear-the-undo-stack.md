---
title: 'Como: limpar a pilha de desfazer | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75b821a757f466045b27b7f52e1900ece3f0b0d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473724"
---
# <a name="how-to-clear-the-undo-stack"></a>Como: limpar a pilha de desfazer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: limpar a pilha de desfazer](https://docs.microsoft.com/visualstudio/extensibility/how-to-clear-the-undo-stack).  
  
O procedimento a seguir explica como limpar a pilha de desfazer.  
  
### <a name="to-clear-the-undo-stack"></a>Para limpar a pilha de desfazer  
  
1.  Para limpar o uso da pilha de desfazer a [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) método. Este é um exemplo disso:  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Como implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)

