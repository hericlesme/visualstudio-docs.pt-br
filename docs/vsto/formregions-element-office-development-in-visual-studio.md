---
title: '&lt;formRegions&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
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
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 87909c1586f631ba598258faaf0c7cd02967519c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `formRegions` elemento o `vstov4` namespace contém as regiões de formulário do Microsoft Office Outlook que estão associados com um suplemento do VSTO.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `formRegions` elemento o `vstov4` namespace contém todos os a `formRegion` elementos de um suplemento do VSTO do Outlook. É necessário apenas para Outlook suplementos do VSTO que incluem regiões de formulário.  
  
 Pode haver apenas um `formRegions` elemento definido em um manifesto de aplicativo.  
  
 O `formRegions` elemento não tem atributos.  
  
 O `formRegions` elemento tem o seguinte elemento.  
  
### <a name="formregion"></a>formRegion  
 Necessário para Outlook suplementos do VSTO que incluem regiões de formulário. O `formRegion` elemento está definido [&#60; formRegion &#62; Elemento &#40; desenvolvimento do Office no Visual Studio &#41; ](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra uma `formRegions` elemento em um manifesto de aplicativo para uma solução do Office de nível de aplicativo implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstov4:formRegions>  
  <vstov4:formRegion  
      name="OutlookAddIn1.FormRegion1">  
    <vstov4:messageClass name="IPM.Note" />  
    <vstov4:messageClass name="IPM.Contact" />  
    <vstov4:messageClass name="IPM.Appointment" />  
  </vstov4:formRegion>  
</vstov4:formRegions>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  