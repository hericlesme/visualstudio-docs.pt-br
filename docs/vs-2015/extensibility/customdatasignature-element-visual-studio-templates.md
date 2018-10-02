---
title: Elemento CustomDataSignature (modelos do Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d1ea1198039d238b8a3bac812d0ed1640c448d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473166"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Elemento CustomDataSignature (modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [elemento CustomDataSignature (modelos do Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/customdatasignature-element-visual-studio-templates).  
  
Especifica a assinatura de texto para localizar os dados personalizados.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<CustomDataSignature >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<CustomDataSignature>"string"</CustomDataSignature>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Categoriza o modelo e a define como ele é exibido em qualquer um de **novo projeto** ou o **Adicionar Novo Item** caixa de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 O texto é uma cadeia de caracteres que tenha a assinatura de texto que é necessário para localizar os dados personalizados.  
  
## <a name="remarks"></a>Comentários  
 `CustomDataSignature` é um elemento opcional.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)

