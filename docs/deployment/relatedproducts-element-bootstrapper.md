---
title: '&lt;RelatedProducts&gt; elemento (Bootstrapper) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 548c1002eae581dc0e231f8dd2e28ee4a8376e27
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; elemento (Bootstrapper)
O `RelatedProducts` elemento define outros produtos que dependem de ou que estão incluídos no produto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `RelatedProducts` elemento é um filho de `Product` elemento. Ele não tem atributos.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 O `DependsOnProduct` elemento significa que o produto atual variam de acordo com o produto e que o produto deve ser instalado antes do ano atual. Ele é um filho de `RelatedProducts` elemento. Um `RelatedProducts` elemento pode ter um ou mais `DependsOnProduct` elementos.  
  
 `DependsOnProduct`tem o seguinte atributo.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Code`|O nome do código do produto incluído, conforme especificado pelo `ProductCode` atributo o `Product` elemento. Para obter mais informações, consulte [ \<produto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 O `EitherProducts` elemento define zero ou mais `DependsOnProduct` elementos, e sem atributos. Pelo menos um `DependsOnProduct` neste conjunto deve ser instalado antes do produto atual. Um `RelatedProducts` elemento pode ter zero ou mais `EitherProducts` elementos.  
  
## <a name="includesproduct"></a>IncludesProduct  
 O `IncludesProduct` elemento significa que um produto é incluído com a instalação atual e não requer uma instalação separada. Ele é um filho de `RelatedProducts` elemento. Um `RelatedProducts` elemento pode ter um ou mais `IncludesProduct` elementos.  
  
 `IncludesProduct`tem o seguinte atributo.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Code`|O nome do código do produto incluído, conforme especificado pelo `ProductCode` atributo o `Product` elemento. Para obter mais informações, consulte [ \<produto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir especifica que o Microsoft Installer é instalado com o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]e, portanto, não será necessário uma instalação separada.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Consulte também  
 [\<Produto > elemento](../deployment/product-element-bootstrapper.md)