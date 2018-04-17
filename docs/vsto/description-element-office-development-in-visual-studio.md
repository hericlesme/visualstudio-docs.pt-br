---
title: '&lt;Descrição&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 13755a20b091696bf741c1f25360941e01b65945
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Descrição&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `description` elemento o `vstov4` namespace armazena a descrição para a solução do Office que aparece na caixa de diálogo COM os suplementos de aplicativos do Microsoft Office.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 Opcional. O `description` elemento o `vstov4` namespace. Ele contém a descrição do que o suplemento que aparece na caixa de diálogo COM os suplementos de aplicativos do Microsoft Office.  
  
 O `description` elemento não tem atributos ou elementos.  
  
## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra o `description` elemento para uma solução de nível de aplicativo implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  