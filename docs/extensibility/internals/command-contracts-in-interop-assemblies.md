---
title: Comando contratos em Assemblies de interoperabilidade | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfb60bb4fdc0a633ecee92c47b8465f794416bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratos de comando em Assemblies de interoperabilidade
O contrato básico para tratamento de comandos por meio de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface é que o ambiente chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para determinar se há suporte para o comando e, em caso afirmativo, para determinar o estado e texto. Em seguida, o ambiente chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para executar o comando.  
  
 O <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método é tratado de forma idêntica para todos os comandos. A comunicação adicional, se necessário (por exemplo, com listas suspensas) é gerenciada por meio da chamada a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método com parâmetros apropriados. A interpretação desses parâmetros depende do comando especificado.  
  
 Se o destino do comando retorna valores de parâmetro de saída, o chamador sempre é responsável por liberar todos os recursos que foram alocados. Como esse parâmetro é um tipo variant, limpando a variante libera os recursos.  
  
 Em casos em que os comandos devem operar dentro de uma janela de hierarquia, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface deve ser usada. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface tem um contrato semelhante com métodos semelhantes: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Como VSPackages adicionar elementos da Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementação](../../extensibility/internals/command-implementation.md)