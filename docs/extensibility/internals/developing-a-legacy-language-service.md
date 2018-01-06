---
title: "Desenvolver um serviço de linguagem herdado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords: language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b7a88c00e980cb86764958886d737d5113dfe1fc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="developing-a-legacy-language-service"></a>Desenvolver um serviço de linguagem herdado
Links estas seção para tópicos que ajudam você criar um serviço de linguagem herdada.  
  
 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar um serviço de idioma, consulte [Editor e extensões de serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso melhorar o desempenho do seu serviço de linguagem e permitem que você aproveite os novos recursos do editor.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modelar um serviço de linguagem herdado](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Fornece um modelo de um serviço de linguagem mínima para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor de núcleo. Você pode usar esse modelo como um guia para criar seu próprio serviço de linguagem.  
  
 [Interfaces do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Discute os objetos necessários para implementar um serviço de linguagem e fornece uma lista de objetos adicionais que você pode usar para fornecer o realce de sintaxe, os dados de método e outros recursos.  
  
 [Interceptar comandos do serviço de linguagem herdado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Descreve como inserir um filtro de comando em seu serviço de linguagem para comandos de interceptação que trataria a exibição de texto.  
  
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Fornece informações sobre como registrar seu serviço de linguagem usando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Suporte do serviço de linguagem para depuração](../../extensibility/internals/language-service-support-for-debugging.md)  
 Descreve como um serviço de idioma pode fornecer recursos para dar suporte a um depurador.  
  
 [Lista de verificação: Criar um serviço de linguagem herdado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Fornece instruções passo a passo para criação e a integração de um serviço de idioma para o editor de núcleo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Descreve como implementar o realce de sintaxe em seu serviço de linguagem.  
  
 [Preenchimento de declaração em um serviço de linguagem herdado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Discute a conclusão de instrução, o processo pelo qual um serviço de linguagem ajuda os usuários a concluir uma palavra-chave do idioma ou um elemento que eles tenham sido iniciados digitando.  
  
 [Informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Descreve como fornecer dicas de método para funções sobrecarregadas e métodos.  
  
 [Como fornecer suporte a texto oculto em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Explica a finalidade de uma região de texto oculto e fornece instruções sobre como implementar uma região de texto oculto.  
  
 [Como fornecer suporte estendido à estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Explica as duas opções que estendem o suporte da estrutura de tópicos para seu idioma além de oferecer suporte a *recolher definições* comando.