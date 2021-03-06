---
title: '&lt;Descrição&gt; elemento (implantação do ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 473ebf814ab65c34ee99cab0cf2cc239e0d013eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460591"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Descrição&gt; elemento (implantação do ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [ &lt;descrição&gt; elemento (implantação do ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/description-element-clickonce-deployment).  
  
Identifica as informações do aplicativo usadas para criar uma presença de shell e um **adicionar ou remover programas** item no painel de controle.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `description` elemento é necessário e está no `urn:schemas-microsoft-com:asm.v1` namespace. Ele não contém nenhum elemento filho e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`publisher`|Necessário. Identifica o nome da empresa usado para o posicionamento do ícone do Windows **inicie** menu e o **adicionar ou remover programas** item no painel de controle, quando a implantação é configurada para instalação.|  
|`product`|Necessário. Identifica o nome completo do produto. Usado como o título para o ícone de instalado no Windows **iniciar** menu.|  
|`suiteName`|Opcional. Identifica uma subpasta dentro de `publisher` pasta no Windows **iniciar** menu.|  
|`supportUrl`|Opcional. Especifica uma URL de suporte que é mostrada na **adicionar ou remover programas** item no painel de controle. Também é criado um atalho para essa URL para o suporte do aplicativo no Windows **iniciar** menu, quando a implantação é configurada para a instalação.|  
  
## <a name="remarks"></a>Comentários  
 O elemento de descrição é necessária em todas as configurações de implantação.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra uma `description` elemento em um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto de implantação. Este exemplo de código é parte de um exemplo maior fornecido para o [manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) tópico.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)



