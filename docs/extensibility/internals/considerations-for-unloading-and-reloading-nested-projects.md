---
title: Considerações para descarregar e recarregar projetos de aninhado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bfe39e82a9f15825a5328fe1950347add9d182bb
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerações para descarregar e recarregando projetos aninhados

Quando você implementa os tipos de projeto aninhado, você deve executar etapas adicionais quando você descarregar e recarregar os projetos. Para notificar corretamente os ouvintes de eventos de solução, você deve aumentar corretamente o `OnBeforeUnloadProject` e `OnAfterLoadProject` eventos.

É um motivo para criar esses eventos para o controle do código fonte (SCC). Você não deseja SCC excluir os itens do servidor e, em seguida, adicioná-los como *novo* se houver um `Get` operação do SCC. Nesse caso, um novo arquivo será carregado fora do SCC. Você precisaria descarregar e recarregar todos os arquivos caso eles são diferentes.

Chamadas de controle do código de origem `ReloadItem`. Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface para chamar `OnBeforeUnloadProject` e `OnAfterLoadProject` para excluir o projeto e recriá-la. Quando você implementar a interface dessa maneira, SCC é informado que o projeto foi excluído temporariamente e adicionado novamente. Portanto, o SCC não funciona no projeto como se o projeto foi *realmente* excluído e adicionado novamente.

## <a name="reloading-projects"></a>Recarregar projetos

Para dar suporte a recarregar projetos aninhados, você implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. Na implementação de `ReloadItem`, feche os projetos aninhados e, em seguida, recriá-los.

Normalmente quando um projeto é recarregado, o IDE gera o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> eventos. No entanto, para projetos aninhados que são excluídos e recarregados, o projeto pai inicia o processo, não o IDE. Como o projeto pai não gerar eventos de solução, e o IDE não possui informações sobre a inicialização do processo, os eventos não são gerados.

Para lidar com esse processo, as chamadas de projeto pai `QueryInterface` no <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface. `IVsFireSolutionEvents` tem funções que indicam o IDE para gerar o `OnBeforeUnloadProject` evento para descarregar o projeto aninhado e, em seguida, gerar o `OnAfterLoadProject` evento para recarregar o projeto mesmo.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Aninhar projetos](../../extensibility/internals/nesting-projects.md)