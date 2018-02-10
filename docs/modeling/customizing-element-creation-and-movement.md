---
title: "Personalizando a criação de elemento e a movimentação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ac29f7b745c9698f6051bce6a7b54a1476bf8a7c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-element-creation-and-movement"></a>Personalizando a criação e o movimento de elementos
Você pode permitir que um elemento ser arrastado para outra, da caixa de ferramentas ou em uma operação de colar ou mover a operação. Você pode fazer com que os elementos movidos vinculados para os elementos de destino, usando as relações que você especificar.  
  
 Uma política de mesclagem element (EMD) Especifica o que acontece quando um elemento de modelo é *mesclada* em outro elemento de modelo. Isso acontece quando:  
  
-   O usuário arrasta da caixa de ferramentas para o diagrama ou uma forma.  
  
-   O usuário cria um elemento usando um menu Adicionar no explorer ou uma forma de compartimento.  
  
-   O usuário move um item de um swimlane para outro.  
  
-   O usuário cola um elemento.  
  
-   Código de programa chama a diretiva de mesclagem do elemento.  
  
 Embora as operações de criação podem parecer estar diferente do que as operações de cópia, na verdade, eles funcionam da mesma maneira. Quando um elemento é adicionado, por exemplo da caixa de ferramentas, um protótipo dele é replicado. O protótipo é mesclado no modelo da mesma maneira como os elementos que foram copiados de outra parte do modelo.  
  
 A responsabilidade de um EMD é decidir como um objeto ou grupo de objetos deve ser mesclado em um local específico no modelo. Em particular, ele decide quais relações devem ser inicializadas para vincular o grupo mesclado no modelo. Você também pode personalizá-lo para definir propriedades e criar objetos adicionais.  
  
 ![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd_merge.png "DSL-EMD_Merge")  
A função de uma diretiva de mesclagem do elemento  
  
 Um EMD é gerado automaticamente quando você define um relacionamento de incorporação. Esse padrão EMD cria uma instância da relação, quando os usuários adicionam novas instâncias filho para o pai. Você pode modificar essas EMDs padrão, por exemplo, adicionando o código personalizado.  
  
 Você também pode adicionar seus próprios EMDs na definição de DSL, para permitir que os usuários arrastar ou colar combinações diferentes de classes mescladas e recebimento.  
  
## <a name="defining-an-element-merge-directive"></a>Definindo uma diretiva de mesclagem do elemento  
 Você pode adicionar as diretivas de mesclagem do elemento para classes de domínio, relações de domínio, formas, conectores e diagramas. Você pode adicionar ou encontrá-los no Pesquisador de objetos de DSL na classe de domínio de recebimento. A classe de recebimento é a classe de domínio do elemento que já está no modelo e, em que o elemento novo ou copiado será mesclado.  
  
 ![DSL&#45;EMD&#95;Details](../modeling/media/dsl-emd_details.png "DSL-EMD_Details")  
  
 O **classe indexação** é a classe de domínio de elementos que podem ser mescladas em membros da classe de recebimento. Instâncias de subclasses da classe indexação também serão mescladas por este EMD, a menos que você defina **aplica-se à subclasses** como False.  
  
 Há dois tipos de diretiva de mesclagem:  
  
-   Um **processo de mesclagem** diretiva especifica as relações pelo qual o novo elemento deve ser vinculado à árvore.  
  
-   Um **Forward mesclar** diretiva redireciona o novo elemento a outro elemento de recebimento, normalmente um pai.  
  
 Você pode adicionar código personalizado para mesclar as diretivas:  
  
-   Definir **aceitar personalizado usa** para adicionar seu próprio código para determinar se uma determinada instância do elemento de indexação deve ser mesclada no elemento de destino. Quando o usuário arrasta da caixa de ferramentas, o ponteiro "inválido" mostra se seu código proíbe a mesclagem.  
  
     Por exemplo, você pode permitir a mesclagem apenas quando o elemento de recebimento está em um estado específico.  
  
-   Definir **mesclagem personalizada usa** para adicionar fornecem o próprio código para definir as alterações feitas no modelo quando a mesclagem é executada.  
  
     Por exemplo, você pode definir propriedades no elemento mesclado usando dados de seu novo local no modelo.  
  
> [!NOTE]
>  Se você escrever código personalizado de mesclagem, ele afeta somente mesclagens que são executadas usando este EMD. Se não houver outros EMDs que a mesclagem do mesmo tipo de objeto, ou se não houver outro código personalizado que cria esses objetos sem usar o EMD, em seguida, ele não é afetado pelo seu código personalizado de mesclagem.  
>   
>  Se você deseja certificar-se de que um novo elemento ou uma nova relação sempre é processada pelo seu código personalizado, considere a possibilidade de definir um `AddRule` na relação incorporada e um `DeleteRule` na classe de domínio do elemento. Para obter mais informações, consulte [regras propagar as alterações no modelo de](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="example-defining-an-emd-without-custom-code"></a>Exemplo: Definindo um EMD sem código personalizado  
 O exemplo a seguir permite que os usuários a criar um elemento e um conector ao mesmo tempo, arrastando da caixa de ferramentas para uma forma existente. O exemplo adiciona um EMD à definição de DSL. Antes dessa modificação, os usuários podem arrastar ferramentas para o diagrama, mas não para formas existentes.  
  
 Os usuários também podem colar elementos para outros elementos.  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Para permitir que os usuários a criar um elemento e um conector ao mesmo tempo  
  
1.  Criar uma novo DSL usando o **mínimo idioma** modelo de solução.  
  
     Quando você executa esse DSL, permite criar formas e conectores entre as formas. Você não pode arrastar um novo **ExampleElement** forma da caixa de ferramentas em uma forma existente.  
  
2.  Para permitir que os usuários para os elementos de mesclagem `ExampleElement` formas, criar um novo EMD no `ExampleElement` classe de domínio:  
  
    1.  Em **DSL Explorer**, expanda **Classes de domínio**. Clique com botão direito `ExampleElement` e, em seguida, clique em **adicionar novo elemento de mesclagem diretiva**.  
  
    2.  Verifique se o **DSL detalhes** janela é aberta, para que você pode ver os detalhes de EMD o novo. (Menu: **exibição**, **outras janelas**, **DSL detalhes**.)  
  
3.  Definir o **indexação classe** na janela de detalhes de DSL, para definir a classe de elementos pode ser mesclada em `ExampleElement` objetos.  
  
     Neste exemplo, selecione `ExampleElements`, de modo que o usuário pode arrastar novos elementos em elementos existentes.  
  
     Observe que a classe de indexação se torna o nome do EMD no Explorer DSL.  
  
4.  Em **direta de processo por meio da criação de links**, adicione dois caminhos:  
  
    1.  Um caminho vincula o novo elemento para o modelo pai. A expressão de caminho que você precisa inserir navega de elemento existente, backup por meio da relação incorporada para o modelo pai. Finalmente, ele especifica a função no novo link para o qual o novo elemento será atribuído. O caminho é o seguinte:  
  
         `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
    2.  Outro caminho vincula o novo elemento ao elemento existente. A expressão de caminho Especifica a relação de referência e a função à qual o novo elemento será atribuído. Esse caminho é o seguinte:  
  
         `ExampleElementReferencesTargets.Sources`  
  
     Você pode usar a ferramenta de navegação do caminho para criar cada caminho:  
  
    1.  Em **direta de processo por meio da criação de links nos caminhos**, clique em  **\<Adicionar caminho >**.  
  
    2.  Clique na seta suspensa à direita do item da lista. Uma exibição de árvore é exibida.  
  
    3.  Expanda os nós na árvore para formar o caminho que você deseja especificar.  
  
5.  Teste o DSL:  
  
    1.  Pressione F5 para recriar e executar a solução.  
  
         Recriando levará mais tempo porque o código gerado será atualizado a partir de modelos de texto de acordo com a nova definição de DSL.  
  
    2.  Quando a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tiver iniciado, abra um arquivo de modelo de seu DSL. Crie alguns elementos de exemplo.  
  
    3.  Arraste do **exemplo elemento** ferramenta em uma forma existente.  
  
         Uma nova forma é exibida e está vinculada a forma com um conector existente.  
  
    4.  Copie uma forma existente. Selecione outra forma e cole.  
  
         Uma cópia da primeira forma é criada.  Ele tem um nome novo e está vinculada a segunda forma com um conector.  
  
 Observe os seguintes pontos deste procedimento:  
  
-   Ao criar diretivas de mesclagem do elemento, você pode permitir que qualquer classe de elemento para aceitar qualquer um dos outros. O EMD é criado na classe de domínio de recebimento e a classe de domínio aceito é especificada no **classe Index** campo.  
  
-   Ao definir caminhos, você pode especificar os links que deve ser usado para conectar o novo elemento ao modelo existente.  
  
     Os links que você especificar deve incluir uma relação incorporada.  
  
-   O EMD afeta a criação da caixa de ferramentas e também operações de colagem.  
  
     Se você escrever código personalizado que cria novos elementos, você pode invocar explicitamente o EMD usando o `ElementOperations.Merge` método. Isso garante que o seu código links novos elementos no modelo da mesma maneira que outras operações. Para obter mais informações, consulte [Personalizando comportamento de cópia](../modeling/customizing-copy-behavior.md).  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>Exemplo: Adicionar código personalizado aceitar a um EMD  
 Adicionando código personalizado para um EMD, você pode definir o comportamento de mesclagem mais complexo. Este exemplo simple impede que o usuário adicionando mais de um número fixo de elementos no diagrama. O exemplo modifica o padrão EMD que acompanha um relacionamento de incorporação.  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Para escrever código personalizado aceitar para restringir o que o usuário pode adicionar  
  
1.  Criar uma DSL usando o **mínimo idioma** modelo de solução. Abra o diagrama de definição de DSL.  
  
2.  No Explorador de DSL, expanda **Classes de domínio**, `ExampleModel`, **diretivas de mesclagem do elemento**. Selecione a política de mesclagem element chamado `ExampleElement`.  
  
     Este EMD controla como o usuário pode criar novos `ExampleElement` objetos no modelo, por exemplo, arrastando da caixa de ferramentas.  
  
3.  No **DSL detalhes** janela, selecione **personalizado usa aceitar**.  
  
4.  Recompile a solução. Esta ação levará mais tempo porque o código gerado será atualizado do modelo.  
  
     Um erro de compilação será relatado, semelhante a: "Company.ElementMergeSample.ExampleElement não contém uma definição para CanMergeExampleElement..."  
  
     Você deve implementar o método `CanMergeExampleElement`.  
  
5.  Criar um novo arquivo de código no **Dsl** projeto. Substituir seu conteúdo com o código a seguir e altere o namespace para o namespace do seu projeto.  
  
    ```csharp  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace Company.ElementMergeSample // EDIT.  
    {  
      partial class ExampleModel  
      {  
        /// <summary>  
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.  
        /// This happens when the user pastes an ExampleElement  
        /// or drags from the toolbox.  
        /// Determines whether the merge is allowed.  
        /// </summary>  
        /// <param name="rootElement">The root element in the merging EGP.</param>  
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>  
        /// <returns>True if the merge is allowed</returns>  
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)  
        {  
          // Allow no more than 4 elements to be added:  
          return this.Elements.Count < 4;  
        }  
      }  
    }  
  
    ```  
  
     Esse exemplo simples restringe o número de elementos que podem ser mescladas no modelo pai. Para as condições mais interessantes, o método pode inspecionar qualquer uma das propriedades e os links do objeto receptor. Ele também pode inspecionar as propriedades dos elementos de mesclagem, que são executadas em um <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Para obter mais informações sobre `ElementGroupPrototypes`, consulte [Personalizando comportamento de cópia](../modeling/customizing-copy-behavior.md). Para obter mais informações sobre como escrever código que lê um modelo, consulte [navegar e atualizar um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
6.  Teste o DSL:  
  
    1.  Pressione F5 para recriar a solução. Quando a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é aberta, abra uma instância do seu DSL.  
  
    2.  Crie novos elementos de várias maneiras:  
  
        1.  Arraste do **exemplo elemento** ferramenta para o diagrama.  
  
        2.  No **Gerenciador de modelos de exemplo**, com o botão direito no nó raiz e, em seguida, clique em **adicionar novo elemento de exemplo**.  
  
        3.  Copie e cole um elemento no diagrama.  
  
    3.  Verifique se você não pode usar qualquer um destes procedimentos para adicionar mais de quatro elementos no modelo. Isso ocorre porque todas elas usam a diretiva de mesclagem do elemento.  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>Exemplo: Adicionar código personalizado de mesclagem para um EMD  
 No código personalizado de mesclagem, você pode definir o que acontece quando o usuário arrasta uma ferramenta ou cola em um elemento. Há duas maneiras de definir uma mesclagem personalizada:  
  
1.  Definir **usa personalizado mesclagem** e forneça o código necessário. Seu código substitui o código gerado de mesclagem. Use esta opção se você quiser redefinir completamente o que faz a mesclagem.  
  
2.  Substituir o `MergeRelate` método e, opcionalmente, o `MergeDisconnect` método. Para fazer isso, você deve definir o **gera duplo derivado** propriedade da classe de domínio. Seu código pode chamar o código de mesclagem gerado na classe base. Use esta opção se você quiser executar operações adicionais após a mesclagem foi executada.  
  
 Essas abordagens afetam apenas as mesclagens que são executadas usando este EMD. Se você quiser afetar todas as maneiras em que o elemento mesclado pode ser criado, uma alternativa é definir um `AddRule` na relação incorporada e um `DeleteRule` na classe de domínio mesclada. Para obter mais informações, consulte [regras propagar as alterações no modelo de](../modeling/rules-propagate-changes-within-the-model.md).  
  
#### <a name="to-override-mergerelate"></a>Substituir MergeRelate  
  
1.  Na definição de DSL, certifique-se de que você definiu o EMD ao qual você deseja adicionar o código. Se desejar, você pode adicionar caminhos e definir personalizado aceitar código conforme descrito nas seções anteriores.  
  
2.  No diagrama DslDefinition, selecione a classe de recebimento da mesclagem. Geralmente é a classe na extremidade de origem de uma relação de incorporação.  
  
     Por exemplo, uma DSL gerada da solução mínima idioma, selecione `ExampleModel`.  
  
3.  No **propriedades** janela, defina **gera duplo derivado** para **true**.  
  
4.  Recompile a solução.  
  
5.  Inspecionar o conteúdo do **Dsl\Generated Files\DomainClasses.cs**. Procure métodos chamados `MergeRelate` e examine seu conteúdo. Isso ajudará você a escrever suas próprias versões.  
  
6.  Em um novo arquivo de código, uma classe parcial para a classe de recebimento de gravação e substituir o `MergeRelate` método. Lembre-se de chamar o método base. Por exemplo:  
  
    ```csharp  
    partial class ExampleModel  
    {  
      /// <summary>  
      /// Called when the user drags or pastes an ExampleElement onto the diagram.  
      /// Sets the time of day as the name.  
      /// </summary>  
      /// <param name="sourceElement">Element to be added</param>  
      /// <param name="elementGroup">Elements to be merged</param>  
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)  
      {  
        // Connect the element according to the EMD:  
        base.MergeRelate(sourceElement, elementGroup);  
  
        // Custom actions:   
        ExampleElement mergingElement = sourceElement as ExampleElement;  
        if (mergingElement != null)  
        {  
          mergingElement.Name = DateTime.Now.ToLongTimeString();  
        }  
      }  
    }  
  
    ```  
  
#### <a name="to-write-custom-merge-code"></a>Para escrever código personalizado de mesclagem  
  
1.  Em **Dsl\Generated Code\DomainClasses.cs**, inspecionar métodos chamados `MergeRelate`. Esses métodos criam vínculos entre um novo elemento e o modelo existente.  
  
     Além disso, inspecionar métodos chamados `MergeDisconnect`. Esses métodos desvincular um elemento do modelo quando ele é a ser excluído.  
  
2.  Em **DSL Explorer**, selecione ou crie a diretiva de mesclagem do elemento que você deseja personalizar. No **DSL detalhes** janela, defina **usa personalizado mesclar**.  
  
     Quando você definir essa opção, o **processo de mesclagem** e **Forward mesclar** opções serão ignoradas. O código é usado em vez disso.  
  
3.  Recompile a solução. Levará mais tempo porque os arquivos de código gerado serão atualizados do modelo.  
  
     Mensagens de erro serão exibida. Clique duas vezes as mensagens de erro para ver as instruções no código gerado. Essas instruções pedir que você forneça dois métodos, `MergeRelate` *YourDomainClass* e `MergeDisconnect` *YourDomainClass*  
  
4.  Os métodos de gravação em uma definição de classe parcial em um arquivo de código separado. Os exemplos que você inspecionou anteriormente devem sugerir que você precisa.  
  
 Código personalizado de mesclagem não afetará o código que cria objetos e relações diretamente, e ele não afete outros EMDs. Para certificar-se de que as alterações adicionais são implementadas independentemente de como o elemento é criado, considere gravar uma `AddRule` e um `DeleteRule` em vez disso. Para obter mais informações, consulte [regras propagar as alterações no modelo de](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="redirecting-a-merge-operation"></a>Redirecionando uma operação de mesclagem  
 Uma diretiva de encaminhamento de mesclagem redireciona o destino de uma operação de mesclagem. Normalmente, o novo destino é o pai de inserção do destino inicial.  
  
 Por exemplo, em uma DSL que foi criada com o modelo de diagrama de componente, portas são inseridas em componentes. Portas são exibidas como pequenas formas da borda de uma forma de componente. O usuário cria portas, arrastando a ferramenta de porta para uma forma de componente. Mas, às vezes, o usuário arrasta erroneamente a ferramenta de porta para uma porta existente, em vez do componente, e a operação falhará. Este é um erro comum quando há várias portas existentes. Para ajudar o usuário para evitar esse inconveniente, você pode permitir portas ser arrastado para uma porta existente, mas a ação redirecionado para o componente pai. A operação funciona como se o elemento de destino foram o componente.  
  
 Você pode criar uma diretiva de encaminhamento de mesclagem na solução de modelo de componente. Se você compilar e executar a solução original, você verá que os usuários podem arrastar qualquer número de **porta de entrada** ou **porta de saída** elementos do **caixa de ferramentas** para um **Componente** elemento. No entanto, não é possível arrastar uma porta para uma porta existente. Os alertas de ponteiro disponível que essa movimentação não são habilitados. No entanto, você pode criar uma diretiva de encaminhamento de mesclagem para que uma porta que seja acidentalmente solto em um existente **porta de entrada** é encaminhado para o **componente** elemento.  
  
#### <a name="to-create-a-forward-merge-directive"></a>Para criar uma diretiva de encaminhamento de mesclagem  
  
1.  Criar um [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solução usando o modelo do componente.  
  
2.  Exibição de **DSL Explorer** abrindo DslDefinition.dsl.  
  
3.  No **DSL Explorer**, expanda **Classes de domínio**.  
  
4.  O **ComponentPort** classe abstrata de domínio é a classe base dos dois **InPort** e **OutPort**. Clique com botão direito **ComponentPort** e, em seguida, clique em **adicionar novo elemento de mesclagem diretiva**.  
  
     Um novo **elemento mesclar diretiva** nó aparece no **diretivas de mesclagem do elemento** nó.  
  
5.  Selecione o **elemento mesclar diretiva** nó e abra o **DSL detalhes** janela.  
  
6.  Na lista de classe de indexação, selecione **ComponentPort**.  
  
7.  Selecione **encaminhar direta para uma classe de domínio diferente**.  
  
8.  Na lista de seleção de caminho, expanda **ComponentPort**, expanda **ComponentHasPorts**e, em seguida, selecione **componente**.  
  
     O novo caminho deve ser semelhante a este:  
  
     **ComponentHasPorts.Component/!Component**  
  
9. Salve a solução e, em seguida, transformar os modelos clicando no botão direito no **Solution Explorer** barra de ferramentas.  
  
10. Criar e executar a solução. Uma nova instância da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é exibida.  
  
11. Em **Solution Explorer**, abra Sample.mydsl. O diagrama e o **ComponentLanguage ferramentas** aparecer.  
  
12. Arraste um **porta de entrada** do **caixa de ferramentas** para outro **porta de entrada.** Em seguida, arraste um **OutputPort** para um **InputPort** e, em seguida, a outro **OutputPort**.  
  
     Você não verá o ponteiro não está disponível e você poderá remover o novo **porta de entrada** em um existente. Selecione a nova **porta de entrada** e arrastá-lo para outro ponto de **componente**.  
  
## <a name="see-also"></a>Consulte também  
 [Navegar e atualizar um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Personalizando as ferramentas e a caixa de ferramentas](../modeling/customizing-tools-and-the-toolbox.md)   
 [Exemplo de diagramas de circuito DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)