---
title: Gerenciamento de desfazer e refazer usando a API herdado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 93bb65fa9865c5ca7386925d2c145f2acbc0993a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137505"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Gerenciamento de desfazer e refazer usando a API herdado
Editores devem oferecer suporte a operações de desfazer que permitem aos usuários reverter suas alterações recentes ao modificar o código. A maioria dos editores implementados em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pode ter suporte de desfazer automaticamente fornecido pelo ambiente de desenvolvimento integrado (IDE).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)  
 Fornece a capacidade de desfazer para editores com único ou vários modos de exibição.  
  
 [Como: limpar a pilha de desfazer](../extensibility/how-to-clear-the-undo-stack.md)  
 Descreve como limpar uma pilha de desfazer.  
  
 [Como: usar o gerenciamento de desfazer vinculado](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora o gerenciamento de desfazer vinculado em seu editor.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornece gerenciamento de desfazer para um editor que dá suporte a vários modos de exibição.  
  
## <a name="related-sections"></a>Seções relacionadas