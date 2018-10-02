---
title: Lista de objetos de janela de propriedades | Microsoft Docs
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
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87592deaec57b5638336cf191f12896cccbcb5b3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475379"
---
# <a name="properties-window-object-list"></a>Lista de objetos de janela Propriedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [lista de objetos de janela de propriedades](https://docs.microsoft.com/visualstudio/extensibility/internals/properties-window-object-list).  
  
A lista de objetos na **propriedades** janela é uma lista suspensa que permite que você altere a seleção para outros objetos disponíveis dentro de um ou mais períodos selecionados. Selecionar um objeto diferente de dentro dessa lista dispara uma chamada para <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> para informar o ambiente de que um novo objeto foi selecionado. As informações exibidas na **propriedades** janela, em seguida, é alterada para mostrar as propriedades associadas ao objeto selecionado recentemente.  
  
## <a name="the-object-list"></a>A lista de objetos  
 A lista de objeto consiste em dois campos: o nome do objeto (exibidas em negrito) e o tipo de objeto.  
  
 O nome do objeto exibido à esquerda do tipo de objeto em negrito é recuperado do objeto em si usando o `Name` propriedade fornecida pelo <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interface. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, o único método no <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, retorna <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> para coclass dessa interface. O **propriedades** janela usa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> para obter o nome da coclass, que é exibido como o nome do objeto na lista suspensa.  
  
 Se o objeto não tiver um `Name` propriedade, um nome não é exibida na área de nome da lista de objetos. Você pode adicionar uma propriedade de nome para o objeto, se você quiser que o nome exibido na lista de objetos.  
  
 Se o objeto COM não implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, o **propriedades** janela exibe o nome da interface no lugar do nome do objeto no lado esquerdo da lista.  
  
## <a name="see-also"></a>Consulte também  
 [Estender as propriedades](../../extensibility/internals/extending-properties.md)

