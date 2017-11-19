---
title: Ferramentas XML no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.xmldesigner
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
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3786e74f9913400e7a95d962c8512d2263d6ae39
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="xml-tools-in-visual-studio"></a>Ferramentas XML no (Visual Studio)
*Extensible Markup Language (XML)* é uma linguagem de marcação que fornece um formato para descrever dados. Isso facilita declarações mais precisas de conteúdo e mais resultados de pesquisa significativos nas diversas plataformas. Além disso, o XML permite a separação da apresentação dos dados. Por exemplo, em HTML, usam-se marcas para dizer ao navegador para exibir dados como negrito ou itálico; em XML, usam-se marcas somente para descrever dados, como nome da cidade, temperatura e pressão barométrica. Em XML, são usadas folhas de estilo como linguagem XSL e CSS (folhas de estilos em cascata) para apresentar os dados em um navegador. O XML separa os dados da apresentação e do processo. Isso permite exibir e processar os dados como desejar, aplicando diferentes folhas de estilo e aplicações.  
  
 O XML é um subconjunto do SGML que é otimizado para entrega na Web. Ele é definido pelo World Wide Web Consortium (W3C). Essa padronização garante que dados estruturados serão uniformes e independentes de aplicativos ou fornecedores.  
  
 O XML está no cerne de muitos recursos do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Os tópicos a seguir indicam os nomes de ferramentas e os recursos relacionados ao XML que são oferecidos no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e no [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Para obter mais informações, consulte o [XML Developer Center](http://go.microsoft.com/fwlink/?LinkID=100176), que fornece a documentação mais recente, informações técnicas, downloads, grupos de notícias e outros recursos para desenvolvedores XML.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Trabalhando com os dados XML](../xml-tools/working-with-xml-data.md)  
 Discute a função do XML na maneira que os dados são tratados em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Depuração de XSLT](../xml-tools/debugging-xslt.md)  
 Fornece links para tópicos sobre o uso do depurador Visual Studio para depurar o XSLT.  
  
## <a name="reference"></a>Referência  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 Expõe o [Editor XML](http://go.microsoft.com/fwlink/?LinkId=228249) árvore por meio de análise [LINQ](http://go.microsoft.com/fwlink/?LinkId=228250) para todos os documentos XML.  
  
 [XML Standards Reference](http://msdn.microsoft.com/en-us/79c78508-c9d0-423a-a00f-672e855de401) (Referência de padrões XML)  
 Fornece informações sobre as tecnologias XML, incluindo XML, Definição de Tipo de Documento (DTD), linguagem XSD do XML e XSLT.  
  
 <xref:System.Xml?displayProperty=fullName>  
 Descreve as classes e outros elementos que compõem o namespace <xref:System.Xml> e fornece links para informações mais detalhadas sobre cada item.  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 Descreve as classes e outros elementos que compõem o namespace <xref:System.Xml.Serialization> e fornece links para informações mais detalhadas sobre cada item.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [XML Document Object Model (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)  
 Descreve como o <xref:System.Xml.XmlDocument> e suas classes associadas atendem a conformidade com as especificações de suporte do namespace do Nível 1 e Nível 2 do W3C Document Object Model (Principal).  
  
 [Leitura de XML com o XmlReader](http://msdn.microsoft.com/en-us/3029834c-a27e-4331-b7aa-711924062182)  
 Descreve como o <xref:System.Xml.XmlReader> fornece acesso somente para leitura, somente para encaminhamento sem armazenamento dos dados XML através de um fluxo XML.  
  
 [Gravando XML com um XmlWriter](http://msdn.microsoft.com/en-us/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 Descreve como o <xref:System.Xml.XmlWriter> fornece uma maneira de gerar fluxos de XML sem armazenamento em cache, somente para encaminhamento, e auxilia na construção de documentos XML em conformidade com a norma W3C.  
  
 [Transformações XSLT](/dotnet/standard/data/xml/xslt-transformations)  
 Descreve como a classe <xref:System.Xml.Xsl.XslCompiledTransform> implementa a recomendação XSLT 1.0.  
  
 [Processar dados XML usando o modelo de dados XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)  
 Descreve como a classe <xref:System.Xml.XPath.XPathNavigator> pode processar os dados XML armazenados em um objeto <xref:System.Xml.XPath.XPathDocument> ou em um <xref:System.Xml.XmlDocument>. A classe <xref:System.Xml.XPath.XPathNavigator> é baseada no Modelo de Dados XQuery 1.0 e XPath 2.0 ou pode ser usada para navegar e editar dados XML.  
  
 [XML Schema Object Model (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som) [SOM (Modelo de Objeto de Esquema) XML]  
 Descreve as classes usadas para criar e manipular esquemas XML, fornecendo uma classe <xref:System.Xml.Schema.XmlSchema> para carregar e editar um esquema.