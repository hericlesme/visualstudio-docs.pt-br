---
title: T4 Diretiva de saída | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e0eaa2d8e3fc257e14e04bad3cac706b8a3bc92a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466089"
---
# <a name="t4-output-directive"></a>T4 Diretiva de saída
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [T4 diretiva de saída](https://docs.microsoft.com/visualstudio/modeling/t4-output-directive).  
  
Em modelos de texto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], a diretiva de `output` é usada pare definir a extensão do nome de arquivo e a codificação do arquivo transformado.  
  
 Por exemplo, se sua [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeto inclui um arquivo de modelo chamado **MyTemplate.tt** que contém a seguinte diretiva:  
  
 `<#@output extension=".cs"#>`  
  
 em seguida [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] irá gerar um arquivo chamado **MyTemplate.cs**  
  
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



