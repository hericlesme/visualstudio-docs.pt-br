---
title: Comentários de código em um serviço de linguagem herdado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b573b464c26c3864cece697191cf03545ada779
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128714"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Comentários de código em um serviço de linguagem herdado
Linguagens de programação normalmente fornecem um meio de anotações ou comentários de código. Um comentário é uma seção de texto que fornece informações adicionais sobre o código, mas é ignorada durante a compilação ou interpretação.  
  
 As classes do framework (MPF) de pacote gerenciado oferecem suporte para comentário e removendo marca de comentário de texto selecionado.  
  
## <a name="comment-styles"></a>Estilos de comentário  
 Há dois estilos gerais de comentário:  
  
1.  Comentários de linha, onde o comentário esteja em uma única linha.  
  
2.  Comentários de bloco, onde o comentário pode incluir várias linhas.  
  
 Comentários de linha normalmente têm um caractere inicial (ou caracteres), enquanto os comentários do bloco têm caracteres iniciais e finais. Por exemplo, no c#, um comentário de linha começa com / /, e inicia um comentário de bloco com / * e termina com \*/.  
  
 Quando o usuário seleciona o comando **comentário de seleção** do **editar** -> **avançado** menu, o comando é roteado para o <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> método o <xref:Microsoft.VisualStudio.Package.Source> classe. Quando o usuário seleciona o comando **seleção Descomente**, o comando é roteado para o <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> método.  
  
## <a name="supporting-code-comments"></a>Suporte a comentários de código  
 Você pode ter seus comentários de código do idioma serviço suporte por meio do `EnableCommenting` chamado parâmetro do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Isso define o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> propriedade o <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Para obter mais informações sobre a configuração de idioma servicce recursos, consulte [registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Você também deve substituir o <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> método para retornar um <xref:Microsoft.VisualStudio.Package.CommentInfo> estrutura com os caracteres de comentário para o seu idioma. C#-caracteres de comentário de linha de estilo são o padrão.  
  
### <a name="example"></a>Exemplo  
 Aqui está um exemplo de implementação do <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> método.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Recursos de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)