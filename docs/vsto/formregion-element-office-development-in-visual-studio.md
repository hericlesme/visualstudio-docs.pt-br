---
title: '&lt;formRegion&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af7dd4f3472692def9f05a937297d54d13c6f0d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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
  
  