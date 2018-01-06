---
title: "Integração com o Editor de XML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5fef7ed581ad39488bc35d9cc46ac211008f5962
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="integration-with-xml-editor"></a>Integração com editor XML
O designer de esquema XML está integrado com o editor XML. Se você modificar um arquivo XSD no Editor de XML, a alteração será refletida no [XML Schema Explorer](../xml-tools/xml-schema-explorer.md). Se você tiver o [exibição de gráfico](../xml-tools/graph-view.md) ou [exibição do modelo de conteúdo](../xml-tools/content-model-view.md) aberto, a alteração também será refletida lá. Você pode navegar entre o designer de esquema XML e o editor XML das seguintes maneiras:  
  
-   No Editor de XML, clique em um nó e selecione **Mostrar em XML Schema Explorer**.  
  
-   Na exibição de gráfico e XML Schema Explorer, clique duas vezes em um nó, ou um nó e selecione **Exibir código**. Na exibição do modelo de conteúdo, clique em um nó e selecione **Exibir código**.  
  
A captura de tela a seguir mostra um esquema XML aberto em XML Schema Explorer. XML Schema Explorer exibe o esquema definido em um modo de exibição de árvore. O editor XML exibe a exibição do texto do nó que está atualmente ativa em XML Schema Explorer.  
  
![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")  
  
Às vezes é útil consulte o código no editor XML e no designer gráfico lado a lado. Para exibir os dois arquivos ao mesmo tempo, clique em qualquer lugar no Editor de XML e selecione **Designer de exibição**. No menu do Windows do Visual Studio, selecione **novo Horizontal (ou Vertical) grupo de guias**.  
  
![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")  
  
## <a name="see-also"></a>Consulte também  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)