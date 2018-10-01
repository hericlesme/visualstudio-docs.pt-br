---
title: Menus de contexto | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b95f913f5705b115473847b12b3fd1df8a5bcff8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467118"
---
# <a name="context-menus"></a>Menus de contexto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Menus de contexto](https://docs.microsoft.com/visualstudio/extensibility/context-menus).  
  
Menus de contexto são exibidos quando um usuário clica com o botão direito em uma região ativa da área de cliente e limpar quando o botão direito do mouse é liberado.  
  
## <a name="editor-context-menus"></a>Menus de Contexto do Editor  
 Interceptando `ECMD_SHOWCONTEXTMENU`, seu serviço de linguagem pode controlar os menus de contexto serão exibido no editor. Para exibir seu próprio menu de contexto, lidar com esse comando quando ele é passado para seus <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Se você não tratar esse comando, o IDE exibirá um menu de contexto padrão fornecido para o editor. Você também pode controlar o conteúdo do menu de contexto em uma base por marcador. Para obter mais informações sobre isso, consulte [usando os marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md) e [interceptar comandos de serviço de linguagem herdado](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Ampliar menus e comandos](../extensibility/extending-menus-and-commands.md)

