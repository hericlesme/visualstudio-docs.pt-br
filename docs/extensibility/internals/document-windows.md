---
title: Documento Windows | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63cbb04310dba0bddea4f6730a6ae5095cbe2612
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="document-windows"></a>Janelas de documento
No Visual Studio, um *janela de documento* é uma janela de quadros filho que está associada uma janela de interface de documentos múltiplos (MDI). Janelas de documento são geralmente usadas para a exibição e a modificação do código-fonte ou texto, mas também podem hospedar outros tipos funcionais. Janelas de documento:  
  
-   Podem ser organizadas em grupos de guia horizontal ou vertical separada no pai MDI para que vários arquivos podem ser exibidos ao mesmo tempo.  
  
-   Pode ser encaixada em qualquer ordem no pai MDI.  
  
-   Pode ser flutuante livremente.  
  
-   São vinculados na ordem de tabulação para outras janelas MDI.  
  
 Os comandos para o agrupamento, Encaixando e flutuando podem ser encontradas no menu de atalho para uma guia da janela de documento.  
  
 Para obter mais informações sobre o comportamento de janela no Visual Studio, consulte [personalizando layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementação de janela de documento  
 Janelas de documento são criadas com a implementação de um editor. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface cria janelas de documento como parte da instanciação de um editor. Para obter mais informações, consulte [Interfaces herdadas no Editor de](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Para fornecer para trás e encaminhar os pontos em uma janela de navegação, implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interface. O editor de texto usa marcadores de texto para identificar os pontos de navegação no documento.  
  
## <a name="the-running-document-table"></a>A tabela de documentos em execução  
 O IDE usa a tabela de documento (RDT) em execução para acompanhar o status de todas as janelas de documento. O RDT é o mecanismo pelo qual documento windows é notificado sobre eventos, como quando uma solução for fechada ou quando um arquivo foi editado. Para obter mais informações, consulte [tabela de documento executando](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Consulte também  
 [Atraso no carregamento do documento](../../extensibility/internals/delayed-document-loading.md)