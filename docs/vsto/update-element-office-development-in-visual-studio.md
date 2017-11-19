---
title: '&lt;atualizar&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a41e7580e7c6c169554bb50c4d0c9af29a992b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;atualizar&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `update` elemento Especifica o intervalo no qual a solução irá verificar atualizações.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `update` elemento é necessário e está no `vstav3` namespace.  
  
 O `update` elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Necessário. Defina habilitado como um dos valores a seguir:<br /><br /> -   **True** para verificar se há atualizações.<br />-   **False** para evitar a verificação de atualizações.|  
  
 O `update` elemento tem os seguintes elementos filho.  
  
### <a name="expiration"></a>expiração  
 O `expiration` elemento é necessário e está no `vstav3` namespace. Este elemento Especifica o intervalo no qual a solução verifica as atualizações.  
  
 O `expiration` elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`maximumAge`|-Necessário. Defina isso como um número inteiro.|  
|`unit`|Necessário. Definir `unit` para um dos seguintes valores:<br /><br /> -   **horas**<br />-   **dias**<br />-   **semanas**|  
  
## <a name="example-of-always-checking-for-updates"></a>Exemplo de sempre verificar atualizações  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra um `update` elemento que é definido como sempre verifique se há atualizações em soluções do Office.  
  
### <a name="code"></a>Código  
  
```  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Exemplo de definição de um intervalo de atualização padrão  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra um `update` elemento em um manifesto de aplicativo para soluções do Office. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Implantando uma solução do Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  