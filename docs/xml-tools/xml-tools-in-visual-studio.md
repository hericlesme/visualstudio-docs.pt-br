---
title: Ferramentas XML no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f823a42d5a89dd22fd273a2971a3b323487a525b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="xml-tools-in-visual-studio"></a>Ferramentas XML no (Visual Studio)

*Extensible Markup Language (XML)* é uma linguagem de marcação que fornece um formato para descrever dados. Isso facilita declarações mais precisas de conteúdo e mais resultados de pesquisa significativos nas diversas plataformas. Além disso, o XML permite a separação da apresentação dos dados. Por exemplo, em HTML, usam-se marcas para dizer ao navegador para exibir dados como negrito ou itálico; em XML, usam-se marcas somente para descrever dados, como nome da cidade, temperatura e pressão barométrica. Em XML, são usadas folhas de estilo como linguagem XSL e CSS (folhas de estilos em cascata) para apresentar os dados em um navegador. O XML separa os dados da apresentação e do processo. Isso permite exibir e processar os dados como desejar, aplicando diferentes folhas de estilo e aplicações.

O XML é um subconjunto do SGML que é otimizado para entrega na Web. Ele é definido pelo World Wide Web Consortium (W3C). Essa padronização garante que dados estruturados serão uniformes e independentes de aplicativos ou fornecedores.

XML é o principal dos muitos recursos do Visual Studio e o .NET Framework. A seguinte lista de tópicos nomeia as ferramentas e recursos relacionados ao XML que são oferecidos no Visual Studio e o .NET Framework.

Para obter mais informações, consulte o <xref:System.Xml?displayProperty=fullName> documentação.

## <a name="in-this-section"></a>Nesta seção

[Trabalhando com os dados XML](../xml-tools/working-with-xml-data.md)  
Discute a função do XML da forma que dados são tratados no Visual Studio.

[Depuração de XSLT](../xml-tools/debugging-xslt.md)  
Fornece links para tópicos sobre o uso do depurador Visual Studio para depurar o XSLT.

## <a name="reference"></a>Referência

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
Expõe o [Editor XML](http://go.microsoft.com/fwlink/?LinkId=228249) árvore por meio de análise [LINQ](http://go.microsoft.com/fwlink/?LinkId=228250) para todos os documentos XML.

[XML Standards Reference](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) (Referência de padrões XML)  
Fornece informações sobre as tecnologias XML, incluindo XML, Definição de Tipo de Documento (DTD), linguagem XSD do XML e XSLT.

<xref:System.Xml?displayProperty=fullName>  
Descreve as classes e outros elementos que compõem o namespace <xref:System.Xml> e fornece links para informações mais detalhadas sobre cada item.

<xref:System.Xml.Serialization?displayProperty=fullName>  
Descreve as classes e outros elementos que compõem o namespace <xref:System.Xml.Serialization> e fornece links para informações mais detalhadas sobre cada item.

## <a name="related-sections"></a>Seções relacionadas

[DOM (Modelo de Objeto do Documento) de XML](/dotnet/standard/data/xml/xml-document-object-model-dom)  
Descreve como o <xref:System.Xml.XmlDocument> e suas classes associadas atendem a conformidade com as especificações de suporte do namespace do Nível 1 e Nível 2 do W3C Document Object Model (Principal).

[Processamento de dados XML com XmlReader e XmlWriter](https://msdn.microsoft.com/library/cc189001(v=vs.95).aspx)

[Transformações XSLT](/dotnet/standard/data/xml/xslt-transformations)  
Descreve como a classe <xref:System.Xml.Xsl.XslCompiledTransform> implementa a recomendação XSLT 1.0.

[Processar dados XML usando o modelo de dados XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)  
Descreve como a classe <xref:System.Xml.XPath.XPathNavigator> pode processar os dados XML armazenados em um objeto <xref:System.Xml.XPath.XPathDocument> ou em um <xref:System.Xml.XmlDocument>. A classe <xref:System.Xml.XPath.XPathNavigator> é baseada no Modelo de Dados XQuery 1.0 e XPath 2.0 ou pode ser usada para navegar e editar dados XML.

[XML Schema Object Model (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som) [SOM (Modelo de Objeto de Esquema) XML]  
Descreve as classes usadas para criar e manipular esquemas XML, fornecendo uma classe <xref:System.Xml.Schema.XmlSchema> para carregar e editar um esquema.