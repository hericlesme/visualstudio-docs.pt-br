---
title: "Considerações para descarregar e recarregar projetos de aninhado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf34a3fe708a6ecab200262224da395b9fa37ecb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerações para descarregar e recarregando projetos aninhados
Quando você implementa os tipos de projeto aninhado, você deve executar etapas adicionais quando você descarregar e recarregar os projetos. Para notificar corretamente os ouvintes de eventos de solução, você deve aumentar corretamente o `OnBeforeUnloadProject` e `OnAfterLoadProject` eventos.  
  
 Um motivo que você deve criar esses eventos dessa maneira é que você não deseja que o controle do código fonte (SCC) para excluir os itens do servidor e, em seguida, adicioná-los de volta como algo novo se não houver um `Get` operação do SCC. Nesse caso, um novo arquivo será carregado fora do SCC e você tem que descarregar e recarregar todos os arquivos caso eles sejam diferentes. Chamadas de SCC `ReloadItem`. Sua implementação dessa chamada é excluir o projeto e recriá-la novamente com a implementação de `IVsFireSolutionEvents` chamar `OnBeforeUnloadProject` e `OnAfterLoadProject`. Quando você executar essa implementação, o SCC é informado que o projeto foi excluído temporariamente e adicionado novamente. Portanto, o SCC não funcionará no projeto como se o projeto foi efetivamente excluído do servidor e, em seguida, adicionado novamente.  
  
## <a name="reloading-projects"></a>Recarregar projetos  
 Para dar suporte a recarregar projetos aninhados, você implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. Na implementação de `ReloadItem`, feche os projetos aninhados e, em seguida, recriá-los.  
  
 Normalmente quando um projeto é recarregado, o IDE gera o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> e `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` eventos. No entanto, para projetos aninhados que serão excluídos e recarregados, o projeto pai inicia o processo, não o IDE. Como o projeto pai não gera eventos de solução, e o IDE não possui informações sobre a inicialização do processo, os eventos não são gerados.  
  
 Para lidar com esse processo, as chamadas de projeto pai `QueryInterface` no <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface desativar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interface. `IVsFireSolutionEvents`tem funções que indicam o IDE para gerar o `OnBeforeUnloadProject` evento para descarregar o projeto aninhado e, em seguida, gerar o `OnAfterLoadProject` evento para recarregar o projeto mesmo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Aninhar projetos](../../extensibility/internals/nesting-projects.md)