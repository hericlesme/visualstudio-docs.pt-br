---
title: '&lt;aplicativo&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <application> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9f20c4c8e6d44c62282f68173ce980f650da2692
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;aplicativo&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `application` elemento o `vstav3` namespace encapsula a descrição de soluções do Office. Os elementos filho são diferentes para personalizações no nível do documento e suplementos do VSTO.  
  
## <a name="syntax-for-document-level-customizations"></a>Sintaxe de personalizações no nível do documento  
  
```  
<application>  
  <customization  
    id  
    <document  
      solutionId  
    />  
  </customization>  
</application>  
```  
  
## <a name="syntax-for-application-level-add-ins"></a>Sintaxe de suplementos do nível do aplicativo  
  
```  
<application>  
  <customization  
    id  
    <appAddin  
      application  
      loadBehavior  
      keyName>  
    <friendlyName></friendlyName>  
    <description></description>  
    <formRegions></formRegions>  
  </customization>  
</application>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `application` elemento o `vstav3` namespace é o nó que encapsula todas as informações de personalização específica que estão contidas no `vstov4` namespace.  
  
 O `application` elemento não tem atributos.  
  
 O `application` elemento tem o seguinte elemento.  
  
### <a name="customization"></a>personalização  
 A função da `customization` elemento o `vstov3` namespace está definido em [&#60; personalização &#62; Elemento &#40; desenvolvimento do Office no Visual Studio &#41; ](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## <a name="document-level-customization-example"></a>Exemplo de personalização de nível de documento  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra uma `application` elemento em uma solução de nível de documento implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:application>  
  <vstov4:customizations   
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
    <vstov4:customization>  
      <vstov4:document   
        solutionId="73e" />  
    </vstov4:customization>  
  </vstov4:customizations>  
</vstav3:application>  
```  
  
## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra uma `application` elemento em uma solução do Office de nível de aplicativo implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:application>  
  <vstov4:customizations   
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
    <vstov4:customization>  
      <vstov4:appAddIn   
        application="Outlook"   
        loadBehavior="3"   
        keyName="ContosoOutlookAddIn">  
        <vstov4:friendlyName>  
          ContosoOutlookAddIn  
        </vstov4:friendlyName>  
        <vstov4:description>  
          ContosoOutlookAddIn - Outlook VSTO Add-in   
          created with Visual Studio Tools for Office  
        </vstov4:description>  
        <vstov4:formRegions>  
          <vstov4:formRegion  
              name="OutlookAddIn1.FormRegion1">  
            <vstov4:messageClass name="IPM.Note" />  
            <vstov4:messageClass name="IPM.Contact" />  
            <vstov4:messageClass name="IPM.Appointment" />  
          </vstov4:formRegion>  
        </vstov4:formRegions>  
      </vstov4:appAddIn>  
    </vstov4:customization>  
  </vstov4:customizations>  
</vstav3:application>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  