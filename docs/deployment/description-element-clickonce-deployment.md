---
title: '&lt;Descrição&gt; elemento (implantação do ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06a8f1a1e5ec5f4663ed999566158d104c6a7364
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31564240"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Descrição&gt; elemento (implantação do ClickOnce)
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
|`publisher`|Necessário. Identifica o nome da empresa usado para o posicionamento do ícone do Windows **iniciar** menu e **adicionar ou remover programas** item no painel de controle, quando a implantação é configurada para instalação.|  
|`product`|Necessário. Identifica o nome do produto completo. Usado como o título para o ícone de instalado no Windows **iniciar** menu.|  
|`suiteName`|Opcional. Identifica uma subpasta dentro do `publisher` pasta nas janelas **iniciar** menu.|  
|`supportUrl`|Opcional. Especifica uma URL de suporte que é exibida no **adicionar ou remover programas** item no painel de controle. Também é criado um atalho para essa URL para o suporte do aplicativo no Windows **iniciar** menu, quando a implantação é configurada para a instalação.|  
  
## <a name="remarks"></a>Comentários  
 O elemento de descrição é necessária em todas as configurações de implantação.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra uma `description` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação. Este exemplo de código é parte de um exemplo maior fornecido para o [manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) tópico.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)