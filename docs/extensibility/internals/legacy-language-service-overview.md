---
title: "Visão geral do serviço de linguagem herdada | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d586851da7d02f89335a3920364e25b7f4876860
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-overview"></a>Visão geral do serviço de linguagem herdada
Um serviço de linguagem fornece suporte de editor que permite que você implemente certos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recursos. As classes de serviço de linguagem gerenciada pacote MPF (estrutura) oferecem suporte completo para recursos usados e suporte parcial para outros recursos.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Recursos com suporte total no MPF  
 As classes de serviço de linguagem MPF suportam os seguintes recursos:  
  
-   Realce de sintaxe  
  
-   Estrutura de tópicos  
  
-   Blocos de código de comentário  
  
-   Correspondência de chaves  
  
-   Trechos de código  
  
-   Propriedades de documento personalizadas  
  
-   Informações de parâmetro do IntelliSense  
  
-   Informações rápidas do IntelliSense  
  
-   Conclusão de membro do IntelliSense  
  
-   Conclusão de palavras do IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Recursos parcialmente suportados no MPF  
 MPF fornece suporte parcial somente para os recursos a seguir. Isso significa que você deve implementar os métodos que são chamados pelo MPF.  
  
-   Reformatar o código. Você fornecer o código que implementa a reformatação.  
  
-   Abrange a validação de pontos de interrupção, identificando código válido. Você fornecer o código que identifica as extensões de código.  
  
-   Suporte do depurador **Autos** janela para exibir variáveis. Você fornece o código que determina o que são exibidas na janela.  
  
-   Suporte a **barra de navegação** para navegação rápida entre os tipos e membros. Implementar e retornar uma classe auxiliar que preenche as listas de **barra de navegação** caixas de combinação.  
  
## <a name="implementation"></a>Implementação  
 Você deve concluir várias etapas para implementar o serviço de linguagem e os recursos de serviço de idioma que você deseja dar suporte para o seu idioma. Essas etapas são discutidas nos tópicos a seguir:  
  
-   [Implementar um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Correspondência de chave em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Estruturar em tópico em um serviço de linguagem herdado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Comentar em código em um serviço de linguagem herdado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Reformatar o código em um serviço de linguagem herdado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Propriedades de documento personalizadas em um serviço de linguagem herdado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Suporte a trechos de código em um serviço de linguagem herdado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Suporte a barra de navegação em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Preenchimento de palavra em um serviço de linguagem herdado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Preenchimento de membro em um serviço de linguagem herdado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Informações rápidas em um serviço de linguagem herdado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Suporte a janela de automáticos em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Validar pontos de interrupção em um serviço de linguagem herdado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Consulte também  
 [Implementar um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Extensibilidade do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-extensibility.md)