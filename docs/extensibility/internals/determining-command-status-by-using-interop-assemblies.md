---
title: Determinar o Status de comando usando Assemblies de interoperabilidade | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4989910fdec968a4a05e2459e6625ee2c15fd9a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128158"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Determinar o Status de comando usando Assemblies de interoperabilidade
Um VSPackage deve manter o controle de estado dos comandos pode manipular. O ambiente não pode determinar quando um comando tratado no seu VSPackage torna-se habilitado ou desabilitado. É responsabilidade do seu VSPackage para informar o ambiente sobre os estados de comando, por exemplo, o estado do geral comandos como **Recortar**, **cópia**, e **colar**.  
  
## <a name="status-notification-sources"></a>Fontes de notificação de status  
 O ambiente recebe informações sobre comandos por meio de 'VSPackages <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método, que é parte da implementação do VSPackage do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. O ambiente chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método VSPackage sob duas condições:  
  
-   Quando um usuário abre um menu principal ou um menu de contexto (clicando), o ambiente executa o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método em todos os comandos no menu para determinar seu estado.  
  
-   Quando o VSPackage solicita que o ambiente de atualizar a interface do usuário (UI) atual. Isso ocorre quando comandos que estiverem visíveis para o usuário, como o **Recortar**, **cópia**, e **colar** na barra de ferramentas padrão de agrupamento, tornam-se habilitados e desabilitados em resposta a ações do usuário e o contexto.  
  
 Desde que o shell hospeda vários VSPackages, desempenho do shell seria inaceitável degradar se foram necessário para sondar cada VSPackage para determinar o status do comando. Em vez disso, o VSPackage ativamente deve notificar o ambiente quando sua interface do usuário é alterado no momento da alteração. Para obter mais informações sobre a notificação de atualização, consulte [atualizar a Interface do usuário](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Falha de notificação de status  
 Falha de seu VSPackage para notificar o ambiente de uma alteração de estado do comando pode colocar a interface do usuário em um estado inconsistente. Lembre-se de que qualquer um dos seus comandos de menu de contexto ou menu pode ser colocado em uma barra de ferramentas pelo usuário. Portanto, atualizar a interface do usuário somente quando abre um menu de contexto ou o menu não é suficiente.  
  
## <a name="see-also"></a>Consulte também  
 [Como VSPackages adicionar elementos da Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementação](../../extensibility/internals/command-implementation.md)