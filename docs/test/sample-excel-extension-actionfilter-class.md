---
title: 'Extensão de exemplo do Excel: classe ActionFilter'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b15c0bbc76076178bdb541571e11a7599a3c46c2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-extension-actionfilter-class"></a>Extensão de exemplo do Excel: classe ActionFilter

Essa classe interna estende a classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> e representa um filtro para as ações do teste em um elemento [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

## <a name="simple-properties"></a>Propriedades Simples

Essas propriedades somente leitura especificam como o filtro de ação de teste deve ser executado pela estrutura de teste de IU codificado. Por exemplo, a propriedade <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fornece o nome do filtro de ação. Outras propriedades obtém a <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> do filtro de ação, o <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, o nome do <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> das ações de teste que são filtradas por esse filtro de ação de teste. Outras indicam se deseja <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> e também se a ação de teste é <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.

## <a name="processrule-method"></a>Método ProcessRule

Esse método é chamado pela estrutura de teste de IU codificado e executa o filtro em relação à <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> fornecida. Essa substituição específica remove uma ação de escolha do mouse em uma célula quando a próxima ação na pilha enviar pressionamentos de teclas para a célula. Em seguida, ele retorna `false`.

## <a name="private-methods"></a>Métodos privados

O método `IsLeftClick` determina se a ação fornecida representa um clique com o botão esquerdo do mouse. O método `AreActionsOnSameExcelCell` determina se duas fornecidas ações são executadas na mesma célula do Excel.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>
- [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
