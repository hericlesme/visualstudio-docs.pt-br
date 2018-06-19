---
title: Elemento CustomDataSignature (modelos do Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f56f9b2ffcb09ea8399b6d949cc781f5a99e7c2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31097322"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Elemento CustomDataSignature (modelos do Visual Studio)
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Categoriza o modelo e define como ele é exibido em qualquer um de **novo projeto** ou **Adicionar Novo Item** caixa de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 O texto é uma cadeia de caracteres que tem a assinatura de texto que é necessário para localizar os dados personalizados.  
  
## <a name="remarks"></a>Comentários  
 `CustomDataSignature` é um elemento opcional.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)