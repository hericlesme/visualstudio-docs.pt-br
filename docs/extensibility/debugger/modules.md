---
title: "Módulos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8371bb2fd985062f6e44d97ae720878ad54b06d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="modules"></a>Módulos
Em termos de arquitetura do depurador, um **módulo**:  
  
-   É um contêiner físico de código, como um arquivo executável ou uma DLL.  
  
-   Pode recarregar seus símbolos e descreva a mesmo. Descrições do módulo são exibidas na janela de módulos do IDE.  
  
-   É representado por um [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interface, criado por um mecanismo de depuração para descrever o módulo.  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)