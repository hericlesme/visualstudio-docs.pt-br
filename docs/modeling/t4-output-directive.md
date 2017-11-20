---
title: "T4 Diretiva de saída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: "4"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: bf96406356799a0953ee34eb736266267fe74510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="t4-output-directive"></a>T4 Diretiva de saída
Em modelos de texto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a diretiva de `output` é usada pare definir a extensão do nome de arquivo e a codificação do arquivo transformado.  
  
 Por exemplo, se seu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto inclui um arquivo de modelo chamado **MyTemplate.tt** que contém a seguinte diretiva:  
  
 `<#@output extension=".cs"#>`  
  
 em seguida, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] irá gerar um arquivo chamado **MyTemplate.cs**  
  
 A diretiva de `output` não é necessária em um modelo de texto de tempo de execução (pré-processado). Ao invés disso, o aplicativo obtém a cadeia de caracteres gerada ao chamar `TextTransform()`. Para obter mais informações, consulte [geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Usando a Diretiva de Saída  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 Não deverá haver mais de uma diretiva de `output` em cada modelo de texto.  
  
## <a name="extension-attribute"></a>atributo de extensão  
 Especifica a extensão do nome de arquivo do arquivo de saída do texto gerado.  
  
 O valor padrão é **. cs**  
  
 Exemplos:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Valores aceitáveis:  
 Qualquer extensão de nome de arquivo válida.  
  
## <a name="encoding-attribute"></a>atributo de codificação  
 Especifica a codificação usada ao gerar o arquivo de saída. Por exemplo:  
  
 `<#@ output encoding="utf-8"#>`  
  
 O valor padrão é a codificação usada pelo arquivo de modelo de texto.  
  
 Valores aceitáveis:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (Padrão do sistema)  
  
 Em geral, é possível usar a cadeia de caracteres do WebName ou o número da CodePage de qualquer uma das codificações retornadas por <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.