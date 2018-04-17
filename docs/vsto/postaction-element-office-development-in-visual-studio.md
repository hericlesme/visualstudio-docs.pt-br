---
title: '&lt;postAction&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2934b0ad761dcd512b21e2424515c06fb896dda5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `postAction` elemento o `vstav3` namespace contém o `entrypoint` elementos e todos os `postActionData` elementos que estão associados com ações de pós-implantação, que são executados após a instalação de soluções do Office.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `postAction` elemento é opcional e está no `vstav3` namespace. Há um `postAction` elemento definido em um manifesto de aplicativo para cada ação de pós-implantação.  
  
 O `postAction` elemento não tem atributos.  
  
 `postAction` tem os seguintes elementos.  
  
### <a name="entrypoint"></a>entryPoint  
 Opcional. A função da `entryPoint` elemento o `vstav3` namespace está definido em [ &#60;pontos&#62; elemento &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### <a name="postactiondata"></a>postActionData  
 Opcional. A função da `postActionData` elemento o `vstav3` namespace está definido em [ &#60;postActionData&#62; elemento &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Exemplo de ação de pós-implantação  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra o `postAction` elemento em um manifesto de aplicativo para uma solução do Office que é implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:postAction>  
  <vstav3:entryPoint   
    class="PostDeploymentAction.PostDeploymentActionSample">  
    <assemblyIdentity   
      name="PostDeploymentAction"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:postActionData>  
  </vstav3:postActionData>  
</vstav3:postAction>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  