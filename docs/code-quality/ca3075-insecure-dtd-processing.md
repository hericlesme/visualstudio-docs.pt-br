---
title: 'CA3075: Processamento do DTD insegura'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b288ba61a4e5ee1d8df60d9ac4c250f2ec7081d2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Processamento do DTD insegura
|||
|-|-|
|NomeDoTipo|InsecureDTDProcessing|
|CheckId|CA3075|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Se você usar instâncias de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> inseguras ou referenciar origens de entidade externa, o analisador poderá aceitar a entrada não confiável e divulgar as informações confidenciais para invasores.

## <a name="rule-description"></a>Descrição da Regra
 Um *definição de tipo de documento (DTD)* é uma das duas maneiras que um analisador XML pode determinar a validade de um documento, conforme definido pelo [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Essa regra buscas propriedades e instâncias onde os dados não confiáveis são aceitos para alertar os desenvolvedores sobre potencial [divulgação de informações](/dotnet/framework/wcf/feature-details/information-disclosure) ameaças, que podem levar à [dos (negação de serviço)](/dotnet/framework/wcf/feature-details/denial-of-service) ataques. Essa regra dispara quando:

-   DtdProcessing está ativado o <xref:System.Xml.XmlReader> instância, o que resolve entidades externas de XML usando <xref:System.Xml.XmlUrlResolver>.

-   O <xref:System.Xml.XmlNode.InnerXml%2A> é definida no XML.

-   <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> propriedade é definida para análise.

-   Não confiável de entrada é processada usando <xref:System.Xml.XmlResolver> em vez de <xref:System.Xml.XmlSecureResolver> .

-   O XmlReader.<xref:System.Xml.XmlReader.Create%2A> método é invocado com um carimbo <xref:System.Xml.XmlReaderSettings> nenhuma instância ou em todos os.

-   <xref:System.Xml.XmlReader> é criado com as configurações padrão inseguras ou valores.

 Em cada um desses casos, o resultado é o mesmo: o conteúdo ou os sistema ou rede de compartilhamentos de arquivos da máquina em que o XML é processado será exposto para o invasor, que pode ser usado como um vetor DoS.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações

-   Capturar e processar todas as exceções de XmlTextReader corretamente para evitar a divulgação de informações de caminho.

-   Use o <xref:System.Xml.XmlSecureResolver> para restringir os recursos que pode acessar o XmlTextReader.

-   Não permitir a <xref:System.Xml.XmlReader> para abrir todos os recursos externos, definindo o <xref:System.Xml.XmlResolver> propriedade **nulo**.

-   Certifique-se de que o <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> propriedade <xref:System.Data.DataViewManager> é atribuído a partir de uma fonte confiável.

 .NET 3.5 e anteriores

-   Desabilitar o processamento de DTD, se você estiver lidando com fontes não confiáveis, definindo o <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> propriedade **true** .

-   Classe XmlTextReader tem uma demanda de herança de confiança total.

 .NET 4 e posterior

-   Evite habilitar DtdProcessing se você estiver lidando com fontes não confiáveis, definindo o <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> propriedade **proibir** ou **ignorar**.

-   Certifique-se de que o método Load () usa uma instância de XmlReader em todos os casos InnerXml.

> [!NOTE]
>  Essa regra pode relatar falsos positivos em algumas instâncias XmlSecureResolver válidas. Estamos trabalhando para resolver esse problema mid 2016.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 A menos que você tiver certeza de que a entrada é conhecida por ser de uma fonte confiável, não suprima uma regra deste aviso.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>Violação

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>Violações

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
    doc.Load(reader);
}
```

### <a name="violation"></a>Violação

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>Violação

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>Violação

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>Violações

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```