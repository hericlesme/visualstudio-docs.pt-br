---
title: '&lt;formRegions&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c51b626c104d5342c00dbd45a2c565315c9c2225
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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
 Necessário para Outlook suplementos do VSTO que incluem regiões de formulário. O `formRegion` elemento está definido [ &#60;formRegion&#62; elemento &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
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
  
  