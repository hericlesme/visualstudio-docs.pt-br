---
title: '&lt;customHostSpecified&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
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
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7ad3bb1e62e2ea98f5afe1de5cc9eb49f711234
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `customHostSpecified` elemento indica que esta solução não é um aplicativo autônomo. Soluções do Office contêm componentes que são hospedados em aplicativos do Microsoft Office.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `customHostSpecified` elemento é necessário para soluções do Office. Elemento de `co.v1` namespace e especifica que essa implantação contém um componente que será implantado dentro de um host personalizado e não é um aplicativo autônomo.  
  
 Esse elemento é um filho do primeiro `<entrypoint>` elemento no manifesto do aplicativo. Não pode haver nenhum outro elemento filho, em que `<entrypoint>` elemento ou [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gerará um erro de validação durante a instalação.  
  
 Este elemento tem sem atributos e nenhum elemento filho.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra o `customHostSpecified` elemento em um manifesto de aplicativo para uma solução do Office. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  