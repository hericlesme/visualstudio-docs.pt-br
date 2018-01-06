---
title: Fornecedores de porta | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0cab184b0ecf4c4971b116cc9dfde26d8f80b45f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="port-suppliers"></a>Fornecedores de porta
Em termos de arquitetura do depurador, um **supplier porta**:  
  
-   Está contido em um servidor e fornece as portas na solicitação ao servidor.  
  
-   Pode adicionar e remover portas do servidor de conteúdo.  
  
-   Pode enumerar todas as portas que ele foi fornecido para o servidor.  
  
-   É representado por um [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interface, que é registrado com o Visual Studio por meio do registro. Essa interface pode ser obtida chamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fornece um fornecedor de porta padrão e uma porta padrão. Se precisar de uma porta personalizada a ser implementada, um fornecedor de porta personalizado também precisa ser implementado para fornecer essas portas personalizadas.  
  
## <a name="see-also"></a>Consulte também  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Portas](../../extensibility/debugger/ports.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)