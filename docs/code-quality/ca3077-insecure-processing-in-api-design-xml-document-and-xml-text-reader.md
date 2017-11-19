---
title: 'CA3077: Processamento inseguro no projeto de API, o documento XML e o leitor de texto XML | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6944b49626771317f1643f7ae521b0db43c2200c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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
 Um [definição de tipo de documento (DTD)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) é uma das duas maneiras que um analisador XML pode determinar a validade de um documento, conforme definido pelo [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Essa regra buscas propriedades e instâncias onde os dados não confiáveis são aceitos para alertar os desenvolvedores sobre potencial [divulgação de informações](/dotnet/framework/wcf/feature-details/information-disclosure) ameaças, que podem levar à [dos (negação de serviço)](/dotnet/framework/wcf/feature-details/denial-of-service) ataques. Essa regra dispara quando:  
  
-   <xref:System.Xml.XmlDocument>ou <xref:System.Xml.XmlTextReader> classes usam valores de resolvedor padrão para o processamento do DTD.  
  
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