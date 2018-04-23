---
title: Informações de parâmetro em um gratuito2 de idioma herdado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6aaf8ba9be9e16eeb979b0d64d3e80e8d70b564f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informações de parâmetro em um serviço de linguagem herdado
Informações de parâmetro de IntelliSense é uma dica de ferramenta que exibe a assinatura de um método quando o usuário digita a lista de parâmetros iniciar caractere (normalmente um parêntese de abertura) para a lista de parâmetros de método. Como cada parâmetro é inserido e o separador de parâmetro (geralmente uma vírgula) for digitado, a dica de ferramenta é atualizada para mostrar o próximo parâmetro em negrito.  
  
 As classes do framework (MPF) de pacote gerenciado oferecem suporte ao gerenciamento de dica de ferramenta de informações do parâmetro. O analisador deve detectar parâmetro Iniciar, parâmetro a seguir, e caracteres de final do parâmetro e ele devem fornecer uma lista de assinaturas de método e seus parâmetros associados.  
  
 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações, consulte [estendendo o Editor e o idioma serviços](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso melhorar o desempenho do seu serviço de linguagem e permitem que você aproveite os novos recursos do editor.  
  
## <a name="implementation"></a>Implementação  
 O analisador deve definir o valor de gatilho <xref:Microsoft.VisualStudio.Package.TokenTriggers> é definido quando encontrar um caractere de início de lista de parâmetro (geralmente um parêntese de abertura). Ele deve ser definido um <xref:Microsoft.VisualStudio.Package.TokenTriggers> disparar quando encontra um separador de parâmetro (geralmente uma vírgula). Isso faz com que uma dica de ferramenta de informações do parâmetro seja atualizado e mostrar o próximo parâmetro em negrito. O analisador deve definir o valor de gatilho <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando se encontra o caractere de final de lista de parâmetro (geralmente um parêntese de fechamento).  
  
 O <xref:Microsoft.VisualStudio.Package.TokenTriggers> valor gatilho inicia uma chamada para o <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> método, que por sua vez chama o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analisador de método com uma razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>. Se o analisador determina se o identificador para a lista de parâmetros iniciar caractere é um nome de método reconhecido, ele retorna uma lista de assinaturas de método em correspondentes a <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto. Se nenhuma assinatura do método forem encontrada, a dica de ferramenta de informações do parâmetro é exibida com a primeira assinatura na lista. Essa dica de ferramenta é atualizada como mais a assinatura é digitado. Quando o caractere de final de lista de parâmetro for digitado, a dica de ferramenta de informações do parâmetro é removida do modo de exibição.  
  
> [!NOTE]
>  Para garantir que a dica de ferramenta de informações do parâmetro está formatada corretamente, você deve substituir as propriedades no <xref:Microsoft.VisualStudio.Package.Methods> classe para fornecer os caracteres apropriados. A base de <xref:Microsoft.VisualStudio.Package.Methods> classe supõe um c#-assinatura de método de estilo. Consulte o <xref:Microsoft.VisualStudio.Package.Methods> classe para obter detalhes sobre como isso pode ser feito.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Habilitar o suporte para as informações de parâmetro  
 Para dar suporte a dicas de ferramenta de informações do parâmetro, você deve definir o `ShowCompletion` parâmetro de nomeado o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> para `true`. O serviço de linguagem lê o valor desta entrada do registro da <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriedade.  
  
 Além disso, o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> propriedade deve ser definida como `true` para a dica de ferramenta de informações do parâmetro a ser mostrado.  
  
### <a name="example"></a>Exemplo  
 Aqui está um exemplo simplificado de detectar os caracteres da lista de parâmetro e definir os gatilhos apropriados. Este exemplo é apenas para fins ilustrativos. Ele pressupõe que o scanner contém um método `GetNextToken` que identifica e retornar tokens de uma linha de texto. O exemplo de código simplesmente define os gatilhos sempre que ele vê o tipo correto de caractere.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Suporte a dica de ferramenta de informações do parâmetro no analisador  
 O <xref:Microsoft.VisualStudio.Package.Source> classe faz algumas suposições sobre o conteúdo de <xref:Microsoft.VisualStudio.Package.AuthoringScope> e <xref:Microsoft.VisualStudio.Package.AuthoringSink> classes quando a dica de ferramenta de informações do parâmetro é exibida e atualizada.  
  
-   O analisador recebe <xref:Microsoft.VisualStudio.Package.ParseReason> quando o caractere de início da lista de parâmetro é digitado.  
  
-   O local especificado no <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto é imediatamente após o caractere inicial de lista de parâmetros. O analisador deve coletar as assinaturas de todas as declarações de método disponíveis em posição e armazená-los em uma lista na sua versão do <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto. Essa lista inclui o nome do método, método tipo (ou no tipo de retorno) e uma lista de possíveis parâmetros. Essa lista é pesquisada posteriormente para a assinatura de método ou assinaturas para exibir na dica de ferramenta de informações do parâmetro.  
  
 O analisador, em seguida, deve analisar a linha especificada pelo <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto para coletar o nome do método que está sendo inserido, bem como a distância ao longo do usuário é digitar os parâmetros. Isso é feito, passando o nome do método para o <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> método no <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto e, em seguida, chamar o <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> método quando a lista de parâmetros Iniciar caracteres é analisado, chamar o <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> método quando a lista de parâmetros próximo caractere é analisado e finalmente chamando o <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> método quando o caractere de final de lista de parâmetro é analisado. Os resultados dessas chamadas de método são usados pela <xref:Microsoft.VisualStudio.Package.Source> classe para atualizar a dica de ferramenta de informações do parâmetro adequadamente.  
  
### <a name="example"></a>Exemplo  
 Aqui está uma linha de texto que o usuário pode inserir. Os números abaixo da linha indicam qual etapa é realizada pelo analisador naquela posição na linha (supondo que a análise esquerda move para a direita). O pressuposto é de que tudo antes da linha já foi analisado para assinaturas de método, incluindo a assinatura do método "testfunc".  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 As etapas que usa o analisador são descritas abaixo:  
  
1.  As chamadas de analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> com o texto "testfunc".  
  
2.  As chamadas de analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  As chamadas de analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  As chamadas de analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.