---
title: "Extensão de amostra do Excel: classe ActionFilter | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: "11"
ms.author: douge
manager: douge
ms.openlocfilehash: 346cb9faddf2bd155c91d9fc72176020ba43197b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="sample-excel-extension-actionfilter-class"></a>Extensão de exemplo do Excel: classe ActionFilter
Essa classe interna estende a classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> e representa um filtro para as ações do teste em um elemento [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## <a name="simple-properties"></a>Propriedades Simples  
 Essas propriedades somente leitura permitem ao desenvolvedor especificar como esse filtro de ação de teste deve ser executado pelo framework de teste de IU codificado. Por exemplo, a propriedade <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fornece o nome do filtro de ação. Outras propriedades obtém a <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> do filtro de ação, o <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, o nome do <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> das ações de teste que são filtradas por esse filtro de ação de teste. Outras indicam se deseja <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> e também se a ação de teste é <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>Método ProcessRule  
 Esse método é chamado pela estrutura de teste de IU codificado e executa o filtro em relação à <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> fornecida. Essa substituição específica remove uma ação de escolha do mouse em uma célula quando a próxima ação na pilha enviar pressionamentos de teclas para a célula. Em seguida, ele retorna `false`.  
  
## <a name="private-methods"></a>Métodos privados  
 O método `IsLeftClick` determina se a ação fornecida representa um clique com o botão esquerdo do mouse. O método `AreActionsOnSameExcelCell` determina se duas fornecidas ações são executadas na mesma célula do Excel.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
