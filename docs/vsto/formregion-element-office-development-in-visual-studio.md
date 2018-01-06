---
title: '&lt;formRegion&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <formRegion> element
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: bc425459cee4b4398ead78939283ab4db6efc134
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `formRegion` elemento o `vstov4` namespace identifica uma região de formulário do Microsoft Office Outlook que está associada com um suplemento do VSTO.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `formRegion` elemento o `vstov4` namespace identifica uma região de formulário que está associada com um suplemento do VSTO do Outlook. É necessário apenas para Outlook suplementos do VSTO que incluem regiões de formulário.  
  
 Pode haver vários `formRegion` elementos definidos dentro de um `formRegions` elemento para um único Add-in do VSTO.  
  
 O `formRegion` elemento tem o seguinte atributo.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Necessário. Identifica o nome da região de formulário.|  
  
 O `formRegion` elemento tem os seguintes elementos filho.  
  
### <a name="messageclass"></a>messageClass  
 O `messageClass` elemento identifica o formulário do Outlook que está associado com a região do formulário.  
  
 O `messageClass` elemento tem o seguinte atributo.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Necessário. Identifica o formulário que está associado com a região do formulário.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra uma `formRegion` elemento em um manifesto de aplicativo para Outlook VSTO e suplementos implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Há três classes de mensagem associados a essa região de um formulário. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)   
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  