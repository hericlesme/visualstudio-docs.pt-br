---
title: Conclusão de palavras em um serviço de linguagem herdado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72ddf4e7c755fdecf562f4c190abfb145e6f9819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="word-completion-in-a-legacy-language-service"></a>Completar palavra em um serviço de linguagem herdado
Completar palavra preenche os caracteres ausentes em uma palavra parcialmente digitada. Se houver somente uma conclusão possível, a palavra é concluída quando o caractere de preenchimento é inserido. Se a palavra parcial corresponde a mais de uma possibilidade, é exibida uma lista de possíveis conclusões. Um caractere de preenchimento pode ser qualquer caractere que não é usado para identificadores.  
  
 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações, consulte [estendendo o Editor e o idioma serviços](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso melhorar o desempenho do seu serviço de linguagem e permitem que você aproveite os novos recursos do editor.  
  
## <a name="implementation-steps"></a>Etapas de implementação  
  
1.  Quando o usuário seleciona **Complete Word** do **IntelliSense** menu, o <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando é enviado para o serviço de linguagem.  
  
2.  O <xref:Microsoft.VisualStudio.Package.ViewFilter> classe captura o comando e chama o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método com a razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  O <xref:Microsoft.VisualStudio.Package.Source> class e então chama o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método para obter a lista de conclusões de palavra possíveis e, em seguida, exibe as palavras em uma dica de ferramenta listam usando o <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
     Se houver apenas uma palavra correspondente, a <xref:Microsoft.VisualStudio.Package.Source> classe completa a palavra.  
  
 Como alternativa, se o scanner retorna o valor de gatilho <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando o primeiro caractere de um identificador é digitado, o <xref:Microsoft.VisualStudio.Package.Source> classe detecta isso e chama o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método com a razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>. Nesse caso, o analisador deve detectar a presença de um caractere de seleção de membro e fornecer uma lista de membros.  
  
## <a name="enabling-support-for-the-complete-word"></a>Habilitar o suporte para completar palavra  
 Para habilitar o suporte para o conjunto de conclusão de palavra de `CodeSense` denominado parâmetro passado para o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> associado com o pacote de idioma do atributo de usuário. Isso define o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriedade o <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 O analisador deve retornar uma lista de declarações em resposta ao valor do motivo análise <xref:Microsoft.VisualStudio.Package.ParseReason>, para a conclusão do word operar.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementando completar palavra no método ParseSource  
 Para completar palavra, o <xref:Microsoft.VisualStudio.Package.Source> classe chama o <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método no <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe para obter uma lista de palavras de possíveis correspondências. Você deve implementar a lista em uma classe que deriva de <xref:Microsoft.VisualStudio.Package.Declarations> classe. Consulte o <xref:Microsoft.VisualStudio.Package.Declarations> classe para obter detalhes sobre os métodos que você deve implementar.  
  
 Se a lista contém apenas uma única palavra, em seguida, a <xref:Microsoft.VisualStudio.Package.Source> classe automaticamente insere essa palavra em vez da palavra parcial. Se a lista contiver mais de uma palavra, a <xref:Microsoft.VisualStudio.Package.Source> classe apresenta uma lista de dica de ferramenta na qual o usuário pode selecionar a opção apropriada.  
  
 Veja também o exemplo de um <xref:Microsoft.VisualStudio.Package.Declarations> na implementação da classe [conclusão de membro em um serviço de linguagem herdado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).