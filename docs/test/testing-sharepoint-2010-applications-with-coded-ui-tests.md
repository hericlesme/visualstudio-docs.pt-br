---
title: Testar aplicativos do SharePoint com testes de IU codificados no Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d70493b6ded2274aaf54257a83a7fd64292a1aa6
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Testar aplicativos do SharePoint com testes de IU codificados

Incluir testes de IU codificados em um aplicativo do SharePoint permite verificar se o aplicativo inteiro, incluindo seus controles de interface do usuário, está funcionando corretamente. Testes de IU codificados também podem validar valores e lógica na interface do usuário.

Para saber mais sobre os benefícios de usar testes de IU codificados, consulte [Usar a automação de interface do usuário para testar o código](../test/use-ui-automation-to-test-your-code.md).

**Requisitos**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Criar um teste de IU codificado para um aplicativo do SharePoint

[Criar testes de IU codificados](../test/use-ui-automation-to-test-your-code.md) para seus aplicativos do SharePoint é o mesmo processo de criar testes para outros tipos de aplicativos. A gravação e a reprodução têm suporte para todos os controles na interface de edição na Web. A interface para a seleção de categorias e as Web parts são controles da Web padrão.

![Web parts do SharePoint](../test/media/cuit_sharepoint.png)

> [!NOTE]
> Se estiver registrando a ação, valide as ações antes de gerar código. Como há vários comportamentos associados à passagem do mouse, ela fica ativada por padrão. Tenha cuidado para remover passagens redundantes de testes de IU codificados. Você pode fazer isso editando o código para o teste ou usando o [Editor de testes de IU codificados](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Testar controles do Office em um aplicativo do SharePoint

Para habilitar a automação de algumas web parts do Office em seu aplicativo do SharePoint, você precisa fazer algumas modificações secundárias no código.

> [!NOTE]
> Não há suporte para testar controles do Visio e do PowerPoint em um aplicativo do SharePoint.

### <a name="excel-cell-controls"></a>Controles de célula do Excel

Para incluir controles de célula do Excel, você deve fazer algumas alterações no código do teste de IU codificado.

> [!WARNING]
> Inserir texto em uma célula do Excel, seguida por uma ação de teclas de direção, não registrará corretamente. Use o mouse para selecionar células.

Se você estiver gravando ações em uma célula vazia, você deverá modificar o código clicando duas vezes na célula e, em seguida, executando uma operação de definição de texto. Isso é necessário porque um clique na célula, seguido por qualquer ação de teclado, ativa o `textarea` dentro da célula. Registrar um `setvalue` na célula vazia pesquisaria o `editbox` que não está presente até que a célula tenha sido clicada. Por exemplo:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

Se você estiver gravando ações em uma célula não vazia, a gravação ficará um pouco mais complicada, porque, no momento em que você adicionar texto a uma célula, um novo controle \<div > é adicionado como um filho da célula. O novo controle \<div > contém o texto que você acabou de inserir. O gravador precisa registrar ações no novo controle \<div>, no entanto, ele não pode porque o novo controle \<div> somente existirá quando o teste for inserido. Você deve fazer as seguintes alterações de código manualmente para corrigir esse problema.

1. Vá para a inicialização de célula e realize as propriedades primárias `RowIndex` e `ColumnIndex`:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Encontre o `HtmlDiv` filho da célula:

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }
    ```

3. Adicione o código para a ação de clicar duas vezes no mouse em `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Adicione código para definir o texto em `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI Automation To Test Your Code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint Solutions](/office-dev/office-dev/create-sharepoint-solutions)
- [Verifying and Debugging SharePoint Code](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)
- [Building and Debugging SharePoint Solutions](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)
- [Profiling the Performance of SharePoint Applications](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)
