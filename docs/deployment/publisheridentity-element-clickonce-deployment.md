---
title: "&lt;publisherIdentity&gt; elemento (implantação do ClickOnce) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 527ab7ae43790f7e824ead33fb601f0f8dee2bf0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; elemento (implantação do ClickOnce)
Contém informações sobre o editor que assinou o manifesto de implantação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `publisherIdentity` elemento é necessário para manifestos assinados. A tabela a seguir mostra os atributos que o `publisherIdentity` oferece suporte ao elemento.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Necessário. Descreve a identidade da parte que esse aplicativo publicado.|  
|`issuerKeyHash`|Necessário. Contém o hash SHA-1 da chave pública do emissor do certificado.|  
  
#### <a name="parameters"></a>Parâmetros  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="subhead"></a>Subtítulo