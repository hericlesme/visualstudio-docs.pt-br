---
title: 'Como: limpar a pilha de desfazer | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59f8d57c0ba0e84107cd0d0290b950b335e5f2b0
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639465"
---
# <a name="how-to-clear-the-undo-stack"></a>Como: limpar a pilha de desfazer
O procedimento a seguir explica como limpar a pilha de desfazer.  
  
## <a name="to-clear-the-undo-stack"></a>Para limpar a pilha de desfazer  
  
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
 [Como: implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)