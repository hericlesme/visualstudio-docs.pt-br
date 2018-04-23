---
title: Interceptando comandos de serviço de linguagem herdado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38f025e9dab6f93d87660a59421cbd778c92165a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="intercepting-legacy-language-service-commands"></a>Interceptando herdado comandos de serviço de linguagem
Com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você pode ter os comandos do serviço interceptação do idioma trataria a exibição de texto. Isso é útil para o comportamento específico do idioma que não gerencia a exibição de texto. Você pode interceptar esses comandos, adicionando um ou mais filtros de comando para a exibição de texto de seu serviço de linguagem.  
  
## <a name="getting-and-routing-the-command"></a>Obtendo e roteamento de comando  
 Um filtro de comando é um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto monitora determinadas sequências de caracteres ou comandos de chave. Você pode associar mais de um filtro de comando com uma exibição de texto simples. Cada modo de exibição de texto mantém uma cadeia de comando filtros. Depois de criar um novo filtro de comando, você adicionar o filtro para a cadeia para a exibição de texto apropriado.  
  
 Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para adicionar o filtro de comando para a cadeia. Quando você chama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] retorna outro filtro de comando para o qual você pode passar os comandos que não processa o filtro de comando.  
  
 Você tem as seguintes opções para tratamento de comando:  
  
-   Tratar o comando e, em seguida, passar o comando para o filtro de comando Avançar na cadeia.  
  
-   Tratar o comando e não passe o comando para o próximo filtro de comando.  
  
-   Não tratar o comando, mas transmitir o comando para o próximo filtro de comando.  
  
-   Ignore o comando. Não tratá-la no filtro atual e não passar para o próximo filtro.  
  
 Para obter informações sobre os comandos que deve tratar o seu serviço de linguagem, consulte [comandos importantes para filtros do serviço de linguagem](../../extensibility/internals/important-commands-for-language-service-filters.md).