---
title: 'CA3076: A execução do Script XSLT insegura'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a6b495572786bc4934d2972dfdfd27642803d3f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: A execução do Script XSLT insegura

|||
|-|-|
|NomeDoTipo|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa

Se você executar transformações de linguagem de folhas de estilo extensível (XSLT) em aplicativos .NET maneira insegura, o processador pode resolver referências URI não confiáveis que podem divulgar informações confidenciais para invasores, levando a negação de serviço e entre sites ataques. Para obter mais informações, consulte [XSLT segurança Considerations(.NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Descrição da Regra

**XSLT** é um padrão de World Wide Web Consortium (W3C) para transformar dados XML. XSLT normalmente é usada para gravar folhas de estilo para transformar dados XML em outros formatos, como HTML, fixa texto de comprimento, texto separado por vírgula ou outro formato XML. Embora proibido por padrão, você poderá habilitá-lo para seu projeto.

Para garantir que você não estiver expondo a superfície de ataque, essa regra sempre que dispara o XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> recebe instâncias combinação insegura de <xref:System.Xml.Xsl.XsltSettings> e <xref:System.Xml.XmlResolver>, que permite o processamento de um script mal-intencionado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações

- Substitua o argumento XsltSettings inseguro XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> ou com uma instância que desabilitou a execução de script e de função do documento.

- Substitua o <xref:System.Xml.XmlResolver> argumento com null ou um <xref:System.Xml.XmlSecureResolver> instância.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos

A menos que você tiver certeza de que a entrada é conhecida por ser de uma fonte confiável, não suprima uma regra deste aviso.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violationmdashuses-xsltsettingstrustedxslt"></a>Violation&mdash;uses XsltSettings.TrustedXslt

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
}
```

### <a name="solutionmdashuse-xsltsettingsdefault"></a>Solução&mdash;usar XsltSettings.Default

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Violação de&mdash;documento função e script de execução não está desabilitada

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Solução&mdash;desabilitar a execução de script e de função do documento

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

## <a name="see-also"></a>Consulte também

[Considerações de segurança XSLT (guia .NET)](/dotnet/standard/data/xml/xslt-security-considerations)