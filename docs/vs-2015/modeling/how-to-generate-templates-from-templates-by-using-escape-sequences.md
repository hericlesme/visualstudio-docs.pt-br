---
title: 'Como: gerar modelos a partir de modelos usando sequências de Escape | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7cc523aed43dfbe3339c3f3cc054c09b39a4f060
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473450"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Como gerar modelos a partir de modelos usando sequências de escape
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: gerar modelos de modelos por usando sequências de Escape](https://docs.microsoft.com/visualstudio/modeling/how-to-generate-templates-from-templates-by-using-escape-sequences).  
  
Você pode criar um modelo de texto que cria outro modelo de texto como sua saída de texto gerado. Para fazer isso, você deve usar sequências de escape para delinear as marcas do modelo de texto. Se você não usar sequências de escape, seu modelo de texto gerada terá um significado predefinido. Para obter mais informações sobre como usar sequências de escape em modelos de texto, consulte [usando sequências de Escape em modelos de texto](../modeling/using-escape-sequences-in-text-templates.md).  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Para gerar um modelo de texto de dentro de um modelo de texto  
  
-   Use a barra invertida (\\) como um caractere de escape para produzir as marcas de marcação necessário dentro do modelo de texto para diretivas, instruções, expressões e classes de recursos em um arquivo de modelo de texto separado.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa caracteres de escape para produzir um modelo de texto de um modelo de texto. O `output` diretiva define o tipo de arquivo de destino para o tipo de arquivo de modelo de texto (. TT).  
  
```csharp  
\<#@ output extension=".tt" \#>  
\<#@ assembly name="System.Xml.dll" \#>  
\<#@ import namespace="System.Xml" \#>  
\<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {\#>  
           \<#= attr.Name \#>  
       \<#}  
     }  
\#>  
```  
  
 A saída de texto gerado é um modelo de texto.  
  
```  
<#@ output extension=".tt" #>  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {#>  
           <#= attr.Name #>  
       <#}  
     }  
#>  
```



