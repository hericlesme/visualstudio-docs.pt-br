---
title: "Acessando theText exibição usando a API herdado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bea908ee04913c5ec56678f1438229e045bf68c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Acessando theText exibição usando a API herdado
Uma exibição de texto é uma apresentação do texto que é armazenado em um buffer de texto. Você pode acessar a exibição de texto usando a API herdada, conforme mostrado na seção a seguir.  
  
## <a name="text-view-object"></a>Objeto de exibição de texto  
 Cada modo de exibição está associado ao seu próprio buffer de texto, e o modo de exibição é uma janela sobre os dados no buffer. O diagrama a seguir mostra as interfaces de chave do objeto de exibição de texto que é representado por <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Objeto de exibição de texto do Visual Studio](../extensibility/media/vstextview.gif "vstextview")  
Objeto de exibição de texto  
  
 O modo de exibição é uma maneira de apresentar o texto no buffer. Isso inclui recursos como quebra automática de linha e a estrutura de tópicos, para que o que você vê no modo de exibição não é uma representação exata do texto no buffer.  
  
 Um modo de exibição permite que outros serviços ou processos para interceptar os comandos de entrada e agir sobre eles antes que o modo de exibição atua neles. O serviço mais comum para isso é um serviço de linguagem. Um serviço de idioma talvez seja necessário, por exemplo, para interceptar o comando para a tecla ENTER para fornecer personalizadas dicas de ferramenta ou o comportamento de recuo.  
  
## <a name="adding-functionality-to-the-text-view"></a>Adicionando funcionalidade para a exibição de texto  
 Você pode personalizar o comportamento do modo de exibição de texto ao manipular os pressionamentos de tecla específicos. Para interceptar os pressionamentos de teclas, você deve implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> em seu objeto e forneça um destino de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) para monitorar e interceptar comandos.  
  
 A exibição de texto usa arquitetura sequencial para filtros de comando. Novos filtros de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objetos) são adicionados à sequência de chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método.  
  
 Notificação de eventos para o modo de texto é fornecida usando o `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interface. Implemente essa interface em seu objeto de cliente para receber a notificação de alterações para a exibição de texto. Expor essa interface para o modo de exibição de texto usando o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interface na exibição de texto para receber a notificação de alterações do modo de exibição.  
  
## <a name="see-also"></a>Consulte também  
 [Alterar configurações de exibição usando a API herdado](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Usando o Gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md)