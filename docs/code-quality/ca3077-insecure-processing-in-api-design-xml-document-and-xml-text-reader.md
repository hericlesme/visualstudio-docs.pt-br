---
title: 'CA3077: Processamento inseguro no projeto de API, o documento XML e o leitor de texto XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21c7d4fcf2ec1e16a225879b7feceef2a61a8161
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918006"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Processamento inseguro no projeto de API, o documento XML e o leitor de texto XML
|||
|-|-|
|NomeDoTipo|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Quando criar uma API derivado do XMLDocument e XMLTextReader, estar atento ao <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Usando as instâncias de DTDProcessing inseguras quando referenciando Resolvendo fontes de entidade externa ou definir valores inseguros no XML pode levar à divulgação de informações.

## <a name="rule-description"></a>Descrição da Regra
 Um *definição de tipo de documento (DTD)* é uma das duas maneiras que um analisador XML pode determinar a validade de um documento, conforme definido pelo [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Essa regra buscas propriedades e instâncias onde os dados não confiáveis são aceitos para alertar os desenvolvedores sobre potencial [divulgação de informações](/dotnet/framework/wcf/feature-details/information-disclosure) ameaças, que podem levar à [dos (negação de serviço)](/dotnet/framework/wcf/feature-details/denial-of-service) ataques. Essa regra dispara quando:

-   <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XmlTextReader> classes usam valores de resolvedor padrão para o processamento do DTD.

-   Nenhum construtor está definido para o XmlDocument ou classes derivadas de XmlTextReader ou nenhum valor seguro é usado para <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações

-   Capturar e processar todas as exceções de XmlTextReader corretamente para evitar a divulgação de informações de caminho.

-   Use <xref:System.Xml.XmlSecureResolver>em vez de XmlResolver para restringir os recursos que pode acessar o XmlTextReader.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 A menos que você tiver certeza de que a entrada é conhecida por ser de uma fonte confiável, não suprima uma regra deste aviso.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```