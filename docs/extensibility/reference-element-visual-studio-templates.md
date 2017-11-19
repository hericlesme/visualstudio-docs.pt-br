---
title: "Referência de elemento (modelos do Visual Studio) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f25b39178141f3e3a40899645a0a1af6c8417ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="reference-element-visual-studio-templates"></a>Elemento de referência (modelos do Visual Studio)
Especifica a referência de assembly para adicionar quando o item é adicionado a um projeto.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Referências >  
 \<Referência >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Especifica informações sobre um assembly, que usa o modelo para adicionar uma referência de assembly para projetos. Deve haver um `Assembly` elemento em cada `Reference` elemento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Referências](../extensibility/references-element-visual-studio-templates.md)|Agrupa as referências de assembly que adiciona o modelo para projetos.|  
  
## <a name="remarks"></a>Comentários  
 O `Reference` é um elemento filho obrigatório de `References`.  
  
 O `Reference` e `References` elementos só podem ser usados em arquivos. vstemplate que têm um `Type` valor de atributo `Item`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o `TemplateContent` elemento de um modelo de item. Esse XML adiciona referências aos assemblies System. dll e System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)