---
title: Eventos de Buffer de texto na API herdado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab2812d30c0f02063e9ed3672e9b01855c77da22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eventos de Buffer de texto na API herdado
O objeto de buffer de texto emite vários eventos diferentes que permitem que você responda às situações diferentes.  
  
 Quando você estiver usando a API herdada, você deve implementar as seguintes interfaces para receber a notificação de alterações para o buffer de texto. Expõe as interfaces para o buffer de texto usando o `IConnectionPointContainer` alterações de interface no buffer de texto para receber notificação da linha do buffer. Para obter mais informações, consulte [como: registrar eventos de Buffer de texto com a API herdado de](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). No caso de `IVsTextStreamEvents` ou `IVsTextLinesEvents` interfaces, as alterações são retornadas em qualquer uma ou duas dimensões coordenadas, respectivamente.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de Buffer de texto  
 A seguir estão as interfaces implementadas pelo objeto de buffer de texto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite a criação de ações compostas (ou seja, ações que são agrupadas em uma unidade de desfazer/refazer único).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita a persistência de dados de documento gerenciados pelo buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornece serviços básicos; usado por muitos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornece leitura e gravação de recursos usando as coordenadas bidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Rápida, fornece acesso sequencial orientado por fluxo de texto no buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornece leitura e gravação de recursos usando coordenadas unidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornece acesso a uma coleção genérica de propriedades. A propriedade mais importante é o nome ou identificador de origem do buffer. Você pode armazenar seus próprios dados aleatórios no buffer com esta interface por criar um GUID e usá-lo como uma chave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Oferece suporte a pontos de conexão para eventos.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces de evento de Buffer de texto  
 A seguir estão as interfaces para notificação de eventos de buffer de texto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica os clientes quando um novo serviço de linguagem é associado um buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica os clientes quando um buffer de texto é inicializado e quando as alterações feitas nos dados no buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica os clientes de alterações para o buffer de texto subjacente em coordenadas unidimensionais.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica os clientes de alterações para o buffer de texto subjacente em coordenadas bidimensionais.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica os clientes de alterações nos dados de usuário.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica os clientes do último gesto de confirmação para acionar o evento e fornece o intervalo de texto alterado. O `IVsPreliminaryTextChangeCommitEvents` interface não será disparada em resposta ao desfazer ou refazer comandos. Eventos acionados apenas para os buffers que tenham um Gerenciador de desfazer. `IVsPreliminaryTextChangeCommitEvents` acionado antes de outros eventos, como uma lista muito, para garantir que os outros eventos que não alteram o texto antes que as alterações sejam confirmadas. O VSPackage deve monitorar o o `IVsPreliminaryTextChangeCommitEvents` interface ou `IVsFinalTextChangeCommitEvents` interface, mas não ambos.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica os clientes do último gesto de confirmação para acionar o evento e fornece o intervalo de texto alterado. O `IVsFinalTextChangeCommitEvents` interface não será disparada em resposta ao desfazer ou refazer comandos. Eventos acionados apenas para os buffers que tenham um Gerenciador de desfazer. `IVsFinalTextChangeCommitEvents` é destinado ao uso somente por serviços de idioma ou outros objetos que têm controle total sobre a edição. O VSPackage deve monitorar o o `IVsPreliminaryTextChangeCommitEvents` interface ou `IVsFinalTextChangeCommitEvents` interface, mas não ambos.|  
  
## <a name="see-also"></a>Consulte também  
 [Acessando o Buffer de texto usando a API herdado](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Como: registrar eventos de Buffer de texto com a API herdado de](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)