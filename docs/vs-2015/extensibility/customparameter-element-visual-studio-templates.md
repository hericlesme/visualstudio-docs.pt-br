---
title: Elemento CustomParameter (modelos do Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d968f255607bd0d98dc83945bfcb555400a1573a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467163"
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento CustomParameter (modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [elemento CustomParameter (modelos do Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/customparameter-element-visual-studio-templates).  
  
Contém um nome de parâmetro personalizado e o valor a ser usado quando um projeto ou item é criado a partir do modelo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Necessário. O nome do parâmetro. O formato dos parâmetros é $*nome*$.|  
|`Value`|Necessário. O valor de substituição para o parâmetro.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Agrupa os parâmetros personalizados devem ser passados para o Assistente de modelo quando o assistente faz as substituições de parâmetro.|  
  
## <a name="remarks"></a>Comentários  
 Quando um modelo contém `CustomParameter` elementos, cada instância do `Name` atributo é substituído pelo `Value` atributo nos arquivos de projeto ou item criados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar vários parâmetros personalizados em um modelo. Quando um projeto ou item é criado de um modelo com os seguintes parâmetros personalizados, todas as instâncias do `$color1$` e `$color2$` no modelo de arquivos serão substituídos pela `Red` e `Blue`, respectivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento CustomParameters (modelos do Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parâmetros de modelo](../ide/template-parameters.md)   
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

