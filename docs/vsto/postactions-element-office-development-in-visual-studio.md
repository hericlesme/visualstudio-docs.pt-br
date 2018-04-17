---
title: '&lt;postActions&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2c4dafa1c5ac7ef296ba388ecdfd93d00afef708
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postActions&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `postActions` elemento do `vstav3` namespace contém tudo o `postAction` elementos que descrevem as ações de pós-implantação, que são executados após a instalação de soluções do Office.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `postActions` elemento é opcional e está no `vstav3` namespace. Há apenas um `postActions` elemento definido em um manifesto de aplicativo.  
  
 O `postActions` elemento não tem atributos.  
  
 `postActions` tem o seguinte elemento.  
  
### <a name="postaction"></a>postAction  
 Opcional. A função da `postAction` elemento o `vstav3` namespace está definido em [ &#60;postAction&#62; elemento &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Exemplo de ação de pós-implantação  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra o `postActions` elemento em um manifesto de aplicativo para uma solução do Office implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:postActions>  
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
</vstav3:postActions>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  