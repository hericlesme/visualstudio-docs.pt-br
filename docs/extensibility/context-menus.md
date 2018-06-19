---
title: Menus de contexto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa957e949127663eca7d4e619919edcc07c7a29b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108554"
---
# <a name="context-menus"></a>Menus de contexto
Menus de contexto são exibidos quando um usuário clica com o botão direito em uma região ativa da área cliente e desmarque quando o botão direito do mouse é liberado.  
  
## <a name="editor-context-menus"></a>Menus de Contexto do Editor  
 Interceptando `ECMD_SHOWCONTEXTMENU`, seu serviço de linguagem pode controlar os menus de contexto que serão exibido no editor. Para exibir seu próprio menu de contexto, lidar com esse comando quando ele é passado para o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Se você não lidar com este comando, o IDE exibe um menu de contexto padrão fornecido para o editor. Você também pode controlar o conteúdo do menu de contexto em uma base por marcador. Para obter mais informações sobre isso, consulte [usando marcadores de texto com a API herdado](../extensibility/using-text-markers-with-the-legacy-api.md) e [interceptando comandos de serviço de linguagem herdado](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Ampliar menus e comandos](../extensibility/extending-menus-and-commands.md)