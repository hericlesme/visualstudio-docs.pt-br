---
title: Formatação automática em um serviço de linguagem herdado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 43d9c59beaddfc6992e7b9e16e0e778be2a6d30f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatação em um serviço de linguagem herdado automática
Com a formatação automática, um serviço de linguagem insere um trecho de código automaticamente quando um usuário começa a digitar uma construção de código conhecidos.  
  
## <a name="automatic-formatting-behavior"></a>Comportamento de formatação automática  
 Por exemplo, quando você digita `if`, o serviço de linguagem insere automaticamente a correspondência de chaves, ou se você pressionar a tecla ENTER, o serviço de linguagem força o ponto de inserção na nova linha para o nível de recuo apropriado, dependendo se anterior linha abre um novo escopo.  
  
 O filtro de comando usado para o resto do serviço de idioma também pode ser usado para formatação automática. Você também pode realçar a correspondência de chaves chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)