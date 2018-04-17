---
title: '&lt;ponto de entrada&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f4bd7a9a119a5e604461f44bb166f19e063ab4af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;ponto de entrada&gt; elemento (desenvolvimento do Office no Visual Studio)
  Cada `entryPoint` elemento o `vstav3` namespace identifica um assembly de personalização deve ser executado quando isso [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aplicativo está instalado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `entryPoint` elemento é necessário e está no `vstav3` namespace.  
  
 Cada `entryPoint` elemento pode conter apenas um assembly de personalização. Pode haver vários `entryPoint` elementos definidos em um manifesto de aplicativo.  
  
 O `entryPoint` elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`class`|Necessário. Identifica um assembly de personalização para ser executado. A sintaxe para esse atributo é *NamespaceName.ClassName*.|  
  
 `entryPoint` tem o seguinte elemento.  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Necessário. O `assemblyIdentity` elemento no `vstav3` namespace refere-se a um existente `assemblyIdentity` elemento o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] o manifesto do aplicativo.  
  
 A função de `assemblyIdentity` e seus atributos é definido em [ &#60;assemblyIdentity&#62; elemento &#40;aplicativo ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
## <a name="document-level-customization-example"></a>Exemplo de personalização de nível de documento  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra `entryPoint` elementos em um aplicativo de manifesto para uma solução de nível de documento implantada usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.ThisWorkbook">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet1">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet2">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet3">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra uma `entryPoint` elemento em um manifesto de aplicativo para uma solução do Office de nível de aplicativo implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:entryPoint   
  class="ContosoOutlookAddIn.ThisAddIn">  
  <assemblyIdentity   
    name="ContosoOutlookAddIn"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  