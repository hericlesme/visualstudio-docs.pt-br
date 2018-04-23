---
title: Comandos e Menus que usam Assemblies de interoperabilidade | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c48ee7eb25fa95789076454c849485f4ac1dc384
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandos e Menus que usam Assemblies de interoperabilidade
Um VSPackage que implementa comandos de menu e barra de ferramentas usando assemblies de interoperabilidade deve:  
  
-   Informe o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) sobre os comandos que ele oferece suporte e se elas estão habilitadas.  
  
-   Aderir às regras (contrato) para lidar com comandos.  
  
-   Implementar explicitamente o tratamento de comando usando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface.  
  
 A seguir descreve como executar essas tarefas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Determinar o status do comando usando assemblies de interoperabilidade](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Descreve como um VSPackage notifica o IDE sobre os comandos que ele oferece suporte e se elas estão habilitadas.  
  
 [Contratos de comando em assemblies de interoperabilidade](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Fornece a definição do comando básico contrato usado por todos os VSPackages implementando comandos usando assemblies de interoperabilidade  
  
 [Implementação](../../extensibility/internals/command-implementation.md)  
 Fornece uma visão geral de como um VSPackage implementa um comando.  
  
 [Registrar manipuladores de comandos do assembly de interoperabilidade](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Descreve as entradas do registro necessárias para notificar o IDE um VSPackage fornece um manipulador de comandos.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Disponibilidade](../../extensibility/internals/command-availability.md)  
 Descreve os critérios que serão usados pelo IDE para determinar quais comandos VSPackage estão disponíveis e qual objeto lida com eles.  
  
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Fornece detalhes sobre como criar uma interface do usuário que usa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] suporte de comando.  
  
 [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Uma visão geral do processo usado para relacionar um objeto com a solicitação de comando corretos.