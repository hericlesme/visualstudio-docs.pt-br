---
title: '&lt;friendlyName&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <friendlyName> element
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8019e2446da0feb23cb12dad1a4bbfd4f8a4920
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `friendlyName` elemento o `vstov4` namespace armazena o nome que aparece na lista de programas instalados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `friendlyName` elemento o `vstov4` namespace. O valor aparecerá na lista de programas instalados no computador e na caixa de diálogo Suplementos do VSTO COM aplicativos do Microsoft Office.  
  
 O `friendlyName` elemento não tem atributos ou elementos filho.  
  
## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra o `friendlyName` elemento em uma solução de nível de aplicativo implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  