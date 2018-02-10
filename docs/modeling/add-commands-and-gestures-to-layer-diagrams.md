---
title: "Adicionar comandos e gestos a diagramas de dependência | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5a8f1a2ff8e5ffc95d885b847a17e6cc16965837
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Adicionar comandos e gestos a diagramas de dependência
Você pode definir os comandos de menu de contexto e gestos manipuladores em diagramas de dependência no Visual Studio. Você pode empacotar essas extensões em um Visual Studio Integration extensão (VSIX) que você pode distribuir para outros usuários do Visual Studio.  
  
 Você pode definir vários manipuladores de comando e gesto no mesmo projeto do Visual Studio se desejar. Você também pode combinar vários esses projetos em uma VSIX. Por exemplo, você pode definir um único VSIX que inclui comandos de camada e uma linguagem específica de domínio.  
  
> [!NOTE]
>  Você também pode personalizar a validação de arquitetura, na fonte de quais usuários o código é comparado com diagramas de dependência. Você deve definir a validação de arquitetura em um projeto do Visual Studio separado. Você pode adicioná-lo para o mesmo VSIX como outras extensões. Para obter mais informações, consulte [adicionar validação de arquitetura personalizada a diagramas de dependência](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
## <a name="requirements"></a>Requisitos  
 Consulte [requisitos](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Definindo um comando ou um gesto de um novo VSIX  
 O método mais rápido de criar uma extensão é usar o modelo de projeto. Isso coloca o código e o manifesto do VSIX no mesmo projeto.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Para definir uma extensão usando um modelo de projeto  
  
1.  Criar um projeto em uma nova solução, usando o **novo projeto** comando o **arquivo** menu.  
  
2.  No **novo projeto** caixa de diálogo **projetos de modelagem**, selecione **camada Designer comando extensão** ou **camada Designer gesto de extensão** .  
  
     O modelo cria um projeto que contém um pequeno exemplo em funcionamento.  
  
3.  Para testar a extensão, pressione **CTRL + F5** ou **F5**.  
  
     Inicia uma instância experimental do Visual Studio. Neste exemplo, crie um diagrama de dependência. A extensão de comando ou gesto deve funcionar neste diagrama.  
  
4.  Feche a instância experimental e modificar o código de exemplo. Para obter mais informações, consulte [navegar e atualizar modelos no código do programa de camada](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
5.  Você pode adicionar mais manipuladores de comando ou gesto no mesmo projeto. Para obter mais informações, consulte uma das seções a seguir:  
  
     [Definindo um comando de Menu](#command)  
  
     [Definir um manipulador de gestos](#gesture)  
  
6.  Para instalar a extensão na instância principal do Visual Studio ou em outro computador, localize o **.vsix** arquivo **bin\\\***. Copie-o para o computador onde você deseja instalá-lo e, em seguida, clique duas vezes nele. Para desinstalá-lo, use **extensões e atualizações** no **ferramentas** menu.  
  
## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Adicionando um comando ou um gesto a um VSIX separado  
 Se você quiser criar um VSIX que contém comandos, validadores de camada e outras extensões, é recomendável que você crie um projeto para definir o VSIX e projetos separados para os manipuladores.
  
#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Para adicionar extensões de camada para um VSIX separado  
  
1.  Crie um projeto de biblioteca de classes em uma solução do Visual Studio nova ou existente. No **novo projeto** caixa de diálogo, clique em **Visual C#** e, em seguida, clique em **biblioteca de classes**. Este projeto será contém o comando ou classes de manipulador de gestos.  
  
    > [!NOTE]
    >  Você pode definir mais de uma classe de manipulador de comando ou gesto na biblioteca de uma classe, mas você deve definir as classes da camada de validação em uma biblioteca de classe separada.  
  
2.  Identifique ou crie um projeto do VSIX em sua solução. Um projeto do VSIX contém um arquivo chamado **source.extension.vsixmanifest**. Para adicionar um projeto do VSIX:  
  
    1.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#**, em seguida, clique em **extensibilidade**e, em seguida, clique em **projeto VSIX**.  
  
    2.  No Gerenciador de soluções, clique com botão direito do projeto VSIX e, em seguida, clique em **definir como projeto de inicialização**.  
  
    3.  Clique em **selecione edições** e certifique-se de que **Visual Studio** é verificada.  
  
3.  Em **source.extension.vsixmanifest**, em **ativos**, adicione o comando ou o gesto de projeto do manipulador como um componente MEF.  
  
    1.  No **ativos**. TAB, escolha **novo**.  
  
    2.  Em **tipo**, selecione **Microsoft.VisualStudio.MefComponent**.  
  
    3.  Em **fonte**, selecione **projeto na solução atual** e selecione o nome do seu projeto do manipulador de comando ou gesto.  
  
    4.  Salve o arquivo.  
  
4.  Retornar para o projeto do manipulador de comando ou gesto e adicione as seguintes referências de projeto.  
  
|**Referência**|**O que isso permite que você faça**|  
|-------------------|------------------------------------|  
|Programa \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll Files\Microsoft Visual Studio [versão]|Criar e editar camadas|  
|Microsoft.VisualStudio.Uml.Interfaces|Criar e editar camadas|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Modificar formas em diagramas|  
|System.ComponentModel.Composition|Definir componentes usando Managed Extensibility Framework (MEF)|  
|Microsoft.VisualStudio.Modeling.Sdk.[version]|Definir as extensões de modelagem|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|Atualizar formas e diagramas|  
  
1.  Edite o arquivo de classe na classe biblioteca projeto c# para conter o código para a sua extensão. Para obter mais informações, consulte uma das seções a seguir:  
  
     [Definindo um comando de Menu](#command)  
  
     [Definir um manipulador de gestos](#gesture)  
  
     Consulte também [navegar e atualizar modelos no código do programa de camada](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
2.  Para testar o recurso, pressione CTRL + F5 ou F5. Uma instância experimental do Visual Studio é aberto. Nesse caso, crie ou abra um diagrama de dependência.  
  
3.  Para instalar o VSIX na instância principal do Visual Studio ou em outro computador, localize o **.vsix** arquivo o **bin** diretório do projeto VSIX. Copie-o para o computador onde você deseja instalar o VSIX. Clique duas vezes no arquivo VSIX no Windows Explorer.  
  
     Para desinstalá-lo, use **extensões e atualizações** no **ferramentas** menu.  
  
##  <a name="command"></a>Definindo um comando de Menu  
 Você pode adicionar mais definições de comandos de menu para um gesto existente ou um projeto de comando. Cada comando é definido por uma classe que tem as seguintes características:  
  
-   A classe é declarada da seguinte maneira:  
  
     `[LayerDesignerExtension]`  
  
     `[Export(typeof(ICommandExtension))]`  
  
     `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`  
  
-   O namespace e o nome da classe não são importantes.  
  
-   Os métodos que implementam `ICommandExtension` são da seguinte maneira:  
  
    -   `string Text {get;}`-O rótulo que aparece no menu.  
  
    -   `void QueryStatus(IMenuCommand command)`-chamado quando o usuário clica o diagrama e determina se o comando deve ser visível e habilitado para a seleção do usuário atual.  
  
    -   `void Execute(IMenuCommand command)`-chamado quando o usuário seleciona o comando.  
  
-   Para determinar a seleção atual, você pode importar `IDiagramContext`:  
  
     `[Import]`  
  
     `public IDiagramContext DiagramContext { get; set; }`  
  
     `...`  
  
     `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`  
  
 Para obter mais informações, consulte [navegar e atualizar modelos no código do programa de camada](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
 Para adicionar um novo comando, crie um novo arquivo de código que contém o exemplo a seguir. Em seguida, testar e editá-lo.  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
  
namespace MyLayerExtension // Change to your preference.  
{  
  // This is a feature for dependency diagrams:  
  [LayerDesignerExtension]  
  // This feature is a menu command:  
  [Export(typeof(ICommandExtension))]  
  // Change the class name to your preference:  
  public class MyLayerCommand : ICommandExtension  
  {  
    [Import]  
    public IDiagramContext DiagramContext { get; set; }  
  
    [Import]  
    public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
    // Menu command label:  
    public string Text  
    {  
      get { return "Duplicate layers"; }  
    }  
  
    // Called when the user right-clicks the diagram.  
    // Defines whether the command is visible and enabled.  
    public void QueryStatus(IMenuCommand command)  
    {   
      command.Visible =   
      command.Enabled = DiagramContext.CurrentDiagram  
        .SelectedShapes.Count() > 0;  
    }  
  
    // Called when the user selects the command.  
    public void Execute(IMenuCommand command)  
    {  
      // A selection of starting points:  
      IDiagram diagram = this.DiagramContext.CurrentDiagram;  
      ILayerModel lmodel = diagram.GetLayerModel();  
      foreach (ILayer layer in lmodel.Layers)  
      { // All layers in model.  
      }  
      // Updates should be performed in a transaction:  
      using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("copy selection"))  
      {  
        foreach (ILayer layer in   
          diagram.SelectedShapes  
            .Select(shape=>shape.GetLayerElement())  
            .Where(element => element is ILayer))  
        {  
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");  
          // Position the shapes:  
          IShape originalShape = layer.GetShape();  
          copy.GetShape().Move(  
            originalShape.XPosition + originalShape.Width * 1.2,  
            originalShape.YPosition);  
        }  
        t.Commit();  
      }  
    }  
  }  
}  
```  
  
##  <a name="gesture"></a>Definir um manipulador de gestos  
 Um manipulador de gestos responde quando o usuário arrasta itens para o diagrama de dependência, e quando o usuário clica duas vezes em qualquer lugar no diagrama.  
  
 O comando existente ou projeto VSIX do manipulador de gesto, você pode adicionar um arquivo de código que define um manipulador de gestos:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
namespace MyLayerExtensions // change to your preference  
{  
  [LayerDesignerExtension]  
  [Export(typeof(IGestureExtension))]  
  public class MyLayerGestureHandler : IGestureExtension  
  {  
  }  
}  
```  
  
 Observe os seguintes pontos sobre manipuladores de gesto:  
  
-   Os membros de `IGestureExtension` são da seguinte maneira:  
  
     **OnDoubleClick** -chamado quando o usuário clica duas vezes em qualquer lugar no diagrama.  
  
     **CanDragDrop** - chamado repetidamente que o usuário move o mouse ao arrastar um item para o diagrama. Ele deve trabalhar rapidamente.  
  
     **OnDragDrop** -chamado quando o usuário solta um item para o diagrama.  
  
-   O primeiro argumento para cada método é um `IShape`, do qual você pode obter o elemento de camada. Por exemplo:  
  
    ```  
    public void OnDragDrop(IShape target, IDataObject data)  
    {  
        ILayerElement element = target.GetLayerElement();  
        if (element is ILayer)  
        {  
            // ...  
        }  
    }  
    ```  
  
-   Manipuladores para alguns tipos de item arrastado já estão definidas. Por exemplo, o usuário pode arrastar itens no Gerenciador de soluções para um diagrama de dependência. Não é possível definir um manipulador de arrastar para esses tipos de item. Nesses casos, seu `DragDrop` métodos não serão chamados.  
  
  
## <a name="see-also"></a>Consulte também  
 [Navegar e atualizar modelos de camada no código do programa](../modeling/navigate-and-update-layer-models-in-program-code.md)   
 [Adicionar validação de arquitetura personalizada a diagramas de dependência](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
