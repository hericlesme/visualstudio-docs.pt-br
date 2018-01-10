---
title: "Extensão de amostra do Excel: classe ActionFilter | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 8f2aa063163898a87ff563a356f6bb389cb07243
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
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
