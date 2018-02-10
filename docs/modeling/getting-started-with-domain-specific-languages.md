---
title: "Guia de Introdução com linguagens específicas do domínio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 68b750735c8f5d5f6bd7f1497565692c8836914c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="getting-started-with-domain-specific-languages"></a>Introdução às linguagens específicas do domínio
Este tópico explica os conceitos básicos de definindo e usando uma linguagem específica de domínio (DSL) criada com o SDK de modelagem para Visual Studio.

> [!NOTE]
> No Visual Studio de 2017, o SDK de transformação de modelo de texto e o SDK do Visual Studio de modelagem são instalados automaticamente quando você instala recursos específicos do Visual Studio. Para obter mais detalhes, consulte [esta postagem de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/12/12/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

Se você for novo no DSLs, recomendamos que você leia o **laboratório de ferramentas de DSL**, que pode ser encontrado neste site: [Visualizaton e SDK de modelagem](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>O que você pode fazer com uma linguagem específica de domínio?  
 Uma linguagem específica de domínio é uma notação, geralmente gráfica, que é projetada para ser usado para uma finalidade específica. Por outro lado, as linguagens como UML são para fins gerais. Em uma DSL, você pode definir os tipos de elemento de modelo e suas relações e como são apresentados na tela.  
  
 Quando você tiver criado uma DSL, você pode distribuí-lo como parte de um pacote de extensão de integração do Visual Studio (VSIX). Os usuários trabalham com DSL no Visual Studio:  
  
 ![Diagrama de árvore de família, caixa de ferramentas e explorer](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 A notação é apenas parte de uma DSL. Junto com a notação, o pacote do VSIX inclui ferramentas que os usuários podem aplicar para ajudar a editar e gerar material de seus modelos.  
  
 Um dos principais aplicativos DSLs é gerar o código do programa, arquivos de configuração e outros artefatos. Especialmente em projetos grandes e linhas de produto, em que diversas variantes de um produto serão criados, a gerar muitos aspectos variável de DSLs pode fornecer um grande aumento na confiabilidade e uma resposta muito rápida para alterações de requisitos.  
  
 O restante desta visão geral é um passo a passo que apresenta as operações básicas de criação e uso de uma linguagem específica de domínio no Visual Studio.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para definir uma DSL, é necessário ter instalados os seguintes componentes:  
  
|||  
|-|-|  
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|SDK de modelagem para Visual Studio||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-dsl-solution"></a>Criando uma solução DSL  
 Para criar uma nova linguagem específica de domínio, você pode criar uma nova solução do Visual Studio usando o modelo de projeto de linguagem específica de domínio.  
  
#### <a name="to-create-a-dsl-solution"></a>Para criar uma solução DSL  
  
1.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
2.  Em **tipos de projeto**, expanda o **outros tipos de projetos** nó e clique em **extensibilidade**.  
  
3.  Clique em **Designer de linguagem específica de domínio**.  
  
     ![Criar caixa de diálogo DSL](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
4.  No **nome** , digite **FamilyTree**. Clique em **OK**.  
  
     O **Assistente de linguagem específica de domínio** abre e exibe uma lista de soluções do modelo DSL.  
  
     Clique em cada modelo para ver uma descrição  
  
     Os modelos são úteis pontos de partida. Cada um deles fornece um trabalho concluído DSL, que você pode editar para atender às suas necessidades. Em geral, você deve escolher o modelo mais próximo de você deseja criar.  
  
5.  Para este passo a passo, escolha o **mínimo idioma** modelo.  
  
6.  Insira uma extensão de nome de arquivo para sua DSL na página do assistente apropriada. Essa é a extensão que será usada pelos arquivos que contêm as instâncias de sua DSL.  
  
    -   Escolha uma extensão que não está associada com qualquer aplicativo em seu computador ou em qualquer computador onde você deseja instalar o DSL. Por exemplo, **docx** e **htm** seria inaceitável arquivo extensões de nome.  
  
    -   O assistente o avisará se a extensão inserida está sendo usada como uma DSL. Considere usar uma extensão de nome de arquivo diferente. Também é possível redefinir a instância Experimental do SDK do Visual Studio para limpar os designers experimentais antigos. Clique em **iniciar**, clique em **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**e, em seguida, **redefinição da Microsoft Instância do Visual Studio 2010 Experimental**.  
  
7.  Inspecione as outras páginas e, em seguida, clique em **concluir**.  
  
     Uma solução é gerada que contém dois projetos. Eles são chamados Dsl e DslPackage. Um arquivo de diagrama é aberto que é nomeado DslDefinition.dsl.  
  
    > [!NOTE]
    >  A maioria do código que você pode ver nas pastas nos dois projetos é gerado de DslDefinition.dsl. Por esse motivo, a maioria das modificações no seu DSL são feitas neste arquivo.  
  
 A interface do usuário agora se assemelha à imagem a seguir.  
  
 ![designer de DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 Essa solução define uma linguagem específica de domínio. Para obter mais informações, consulte [visão geral da Interface do usuário específica de domínio idioma ferramentas](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>As partes importantes da solução DSL  
 Observe os seguintes aspectos da nova solução.  
  
-   **Dsl\DslDefinition.DSL** esse é o arquivo que você vê quando você cria uma solução DSL. Quase todo o código na solução é gerado a partir desse arquivo, e a maioria das alterações feitas em uma definição de DSL é feita aqui. Para obter mais informações, consulte Working with a [trabalhando com o diagrama de definição de DSL](../modeling/working-with-the-dsl-definition-diagram.md).  
  
-   **Projeto de DSL** este projeto contém o código que define a linguagem específica de domínio.  
  
-   **Projeto DslPackage** este projeto contém código que permite que instâncias de DSL para ser aberto e editado no Visual Studio.  
  
##  <a name="Debugging"></a>Executando o DSL  
 Você pode executar a solução DSL assim que você criou. Posteriormente, você pode modificar a definição de DSL gradualmente, o que executa a solução novamente após cada alteração.  
  
#### <a name="to-experiment-with-the-dsl"></a>Para fazer experiências com a DSL  
  
1.  Clique em **transformar todos os modelos** na barra de ferramentas do Gerenciador de soluções. Isso gera novamente a maior parte do código-fonte do DslDefinition.dsl.  
  
    > [!NOTE]
    >  Sempre que alterar DslDefinition.dsl, você deve clicar em **transformar todos os modelos** antes de recriar a solução. Você pode automatizar esta etapa. Para obter mais informações, consulte [como automatizar a transformação de todos os modelos](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).
  
2.  Pressione F5, ou o **depurar** menu, clique em **iniciar depuração**.  
  
     O DSL compila e é instalado na instância experimental do Visual Studio.
  
     Inicia uma instância experimental do Visual Studio. A instância experimental terá as configurações de uma subárvore separada do registro, em que as extensões do Visual Studio são registradas para fins de depuração. Instâncias normais do Visual Studio não tem acesso às extensões registrado nele.  
  
3.  Na instância experimental do Visual Studio, abra o arquivo de modelo chamado **teste** de **Gerenciador de soluções**.  
  
     \- ou -  
  
     Clique com botão direito no projeto de depuração, aponte para **adicionar**e, em seguida, clique em **Item**. No **Adicionar Item** caixa de diálogo, selecione o tipo de arquivo de seu DSL.  
  
     O arquivo de modelo é aberto como um diagrama em branco.  
  
     A caixa de ferramentas é aberto e exibe ferramentas apropriadas para o tipo de diagrama.  
  
4.  Use as ferramentas para criar formas e conectores no diagrama.  
  
    1.  Para criar formas, arraste da ferramenta de forma de exemplo para o diagrama.  
  
    2.  Para conectar duas formas, clique na ferramenta de conector de exemplo, clique na primeira forma e, em seguida, clique na segunda forma.  
  
5.  Clique nos rótulos de formas para alterá-los.  
  
 O Visual Studio experimental será parecida com o exemplo a seguir:  
  
 ![](../modeling/media/dsl_min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>O conteúdo de um modelo  
 O conteúdo de um arquivo que é uma instância de uma DSL é chamado um *modelo*. O modelo contém *modelo * * elementos* e *links* entre os elementos. A definição de DSL Especifica quais tipos de elementos de modelo e links podem existir no modelo. Por exemplo, em uma DSL criada usando o modelo de idioma mínima, há um tipo de elemento de modelo e um tipo de link.  
  
 A definição de DSL pode especificar como o modelo é exibido em um diagrama. Você pode escolher entre uma variedade de estilos de formas e conectores. Você pode especificar que algumas formas aparecem dentro de outras formas.  
  
 Você pode exibir um modelo como uma árvore no **Explorer** exibir enquanto você estiver editando um modelo. Como adicionar formas no diagrama, os elementos do modelo também aparecem no explorer. O Pesquisador de objetos pode ser usado mesmo se houver um diagrama.  
  
 Se você não vir o Pesquisador de objetos na instância de depuração do Visual Studio, no **exibição** menu, aponte para **outras janelas**e, em seguida, clique em  *\<seu idioma >* **Explorer**.  
  
### <a name="the-api-of-your-dsl"></a>A API de seu DSL  
 O DSL gera uma API que permite ler e atualizar modelos que são instâncias de DSL. É um aplicativo da API gerar arquivos de texto de um modelo. Para obter mais informações, consulte [geração de código de tempo de Design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Na solução de depuração, abra os arquivos de modelo com a extensão ". TT". Esses exemplos demonstram como gerar o texto de modelos e que você teste a API de seu DSL. Um dos exemplos é gravado [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], o outro na [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
 Em cada modelo de arquivo é o arquivo gerado. Expanda o arquivo de modelo no Gerenciador de soluções e abra o arquivo gerado.  
  
 O arquivo de modelo contém um breve segmento de código que lista todos os elementos no modelo.  
  
 O arquivo gerado contém o resultado.  
  
 Quando você alterar um arquivo de modelo, você verá as alterações correspondentes nos arquivos gerados após você regenerar os arquivos.  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Para gerar novamente os arquivos de texto depois de alterar o arquivo de modelo  
  
1.  Na instância experimental do Visual Studio, salve o arquivo de modelo.  
  
2.  Certifique-se de que o parâmetro de nome de arquivo em cada arquivo. TT refere-se para o arquivo de modelo que você está usando para experiências. Salve o arquivo. tt.  
  
3.  Clique em **transformar todos os modelos de** na barra de ferramentas de **Gerenciador de soluções**.  
  
     \- ou -  
  
     Clique com botão direito os modelos que você deseja gerar novamente e, em seguida, clique em **executar personalizado ferramenta**.  
  
 Você pode adicionar qualquer número de arquivos de modelo de texto para um projeto. Cada modelo gera um arquivo de resultados.  
  
> [!NOTE]
>  Quando você alterar a definição de DSL, o código de modelo de texto de exemplo não funcionará a menos que você atualizá-lo.  
  
 Para obter mais informações, consulte [código de geração de uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md) e [escrevendo código para personalizar uma linguagem específica do domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
## <a name="customizing-the-dsl"></a>Personalizando a DSL  
 Quando você quiser modificar a definição de DSL, feche a instância experimental e atualizar a definição na instância principal do Visual Studio.  
  
> [!NOTE]
>  Depois que você modificou a definição de DSL, você pode perder informações nos modelos de teste que você criou usando versões anteriores.  Por exemplo, a solução de depuração contém um arquivo chamado Sample, que contém algumas formas e conectores. Depois de você começa a desenvolver sua definição de DSL, não estarão visíveis, e eles serão perdidos quando você salvar o arquivo.  
  
 Você pode fazer uma ampla variedade de extensões para o DSL. Os exemplos a seguir oferecem uma impressão das possibilidades.  
  
 Após cada alteração, salve a definição de DSL, clique em **transformar todos os modelos de** na **Solution Explorer**e, em seguida, pressione **F5** para fazer experiências com a DSL alterado.  
  
### <a name="rename-the-types-and-tools"></a>Renomeie os tipos e ferramentas  
 Renomeie as classes de domínio existentes e as relações. Por exemplo, a partir de uma definição de Dsl criados usando o modelo de idioma mínimo, você pode executar as seguintes operações de renomeação, para tornar o DSL representar árvores de família.  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>Para renomear o domínio de classes, relacionamentos e ferramentas  
  
1.  No diagrama DslDefinition, renomeie **ExampleModel** para **FamilyTreeModel**, **ExampleElement** para **pessoa**,  **Destinos** para **pais**, e **fontes** para **filhos**. Você pode clicar em cada rótulo para alterá-la.  
  
     ![Diagrama de definição de DSL &#45; modelo de árvore de família](../modeling/media/familyt_person.png "FamilyT_Person")  
  
2.  Renomeie as ferramentas de elemento e o conector.  
  
    1.  Abra a janela Gerenciador de DSL clicando na guia no Gerenciador de soluções. Se você não pode vê-lo, no **exibição** menu, aponte para **outras janelas** e, em seguida, clique em **DSL Explorer**. Gerenciador de DSL só é visível quando o diagrama de definição de DSL é a janela ativa.  
  
    2.  Abra a janela Propriedades e posicione-o para que você possa ver DSL Pesquisador de objetos e propriedades ao mesmo tempo.  
  
    3.  No Explorador de DSL, expanda **Editor**, **guias da caixa de ferramentas**,  *\<seu DSL >*e, em seguida, **ferramentas**.  
  
    4.  Clique em **ExampleElement**. Este é o item de caixa de ferramentas que é usado para criar elementos.  
  
    5.  Na janela Propriedades, altere o **nome** propriedade **pessoa**.  
  
         Observe que o **legenda** propriedade também será alterado.  
  
    6.  Da mesma maneira, alterar o nome do **ExampleConnector** ferramenta para **ParentLink**. Alterar o **legenda** para que ele não é uma cópia da propriedade de nome de propriedade. Por exemplo, digite **Link pai**.  
  
3.  Recrie o DSL.  
  
    1.  Salve o arquivo de definição de DSL.  
  
    2.  Clique em **transformar todos os modelos** na barra de ferramentas do Gerenciador de soluções  
  
    3.  Pressione F5. Aguarde até que a instância experimental do Visual Studio é exibida.  
  
4.  A solução de depuração na instância experimental do Visual Studio, abra um arquivo de modelo de teste. Arraste elementos para ele na caixa de ferramentas. Observe que as legendas de ferramenta e os nomes de tipo no Pesquisador de objetos de DSL foram alteradas.  
  
5.  Salve o arquivo de modelo.  
  
6.  Abrir um arquivo. TT e substitua as ocorrências dos nomes de tipo e a propriedade antigas com os novos nomes.  
  
7.  Certifique-se de que o nome do arquivo especificado no arquivo. TT especifica seu modelo de teste.  
  
8.  Salve o arquivo. tt. Abra o arquivo gerado para ver o resultado da execução do código no arquivo. tt. Verifique se ele está correto.  
  
### <a name="add-domain-properties-to-classes"></a>Adicionar propriedades de domínio para Classes  
 Adicione propriedades a uma classe de domínio, por exemplo, para representar os anos de nascimento e morte de uma pessoa.  
  
 Para que as novas propriedades visíveis no diagrama, você deve adicionar *decoradores* à forma que exibe o elemento de modelo. Você também deve mapear as propriedades para os decoradores.  
  
##### <a name="to-add-properties-and-display-them"></a>Para adicionar propriedades e exibi-los  
  
1.  Adicione as propriedades.  
  
    1.  No diagrama de definição de DSL, com o botão direito do **pessoa** classe de domínio, aponte para **adicionar**e, em seguida, clique em **propriedade de domínio**.  
  
    2.  Digite uma lista de novos nomes de propriedade, como **nascimento** e **morte**. Pressione **Enter** após cada um deles.  
  
2.  Adicione os decoradores que exibirão as propriedades da forma.  
  
    1.  Siga a linha cinza que estende a classe de domínio da pessoa para o outro lado do diagrama. Isso é um mapa de elemento do diagrama. Vincula a classe de domínio a uma classe de forma.  
  
    2.  Essa classe de forma de atalho, aponte para **adicionar**e, em seguida, clique em **texto decorador**.  
  
    3.  Adicione dois decoradores com nomes como **BirthDecorator** e **DeathDecorator**.  
  
    4.  Selecione cada novo decorator e na janela Propriedades, defina o **posição** campo. Isso determina qual o valor da propriedade de domínio será exibido na forma. Por exemplo, definir **InnerBottomLeft** e **InnerBottomRight**.  
  
         ![Definição de forma do compartimento](../modeling/media/familyt_compartment.png "FamilyT_Compartment")  
  
3.  Mapear os decoradores para as propriedades.  
  
    1.  Abra a janela de detalhes de DSL. Geralmente, é uma guia ao lado da janela de saída. Se você não pode vê-lo, no **exibição** , aponte para **outras janelas**e, em seguida, clique em **DSL detalhes**.  
  
    2.  No diagrama de definição de DSL, clique na linha que conecta o **pessoa** classe de domínio com a classe de forma.  
  
    3.  Em **DSL detalhes**, no **decorador mapas** guia, clique na caixa de seleção em um decorador não mapeado. Em **propriedade Display**, selecione a propriedade de domínio ao qual você deseja que ela está mapeada. Por exemplo, mapear **BirthDecorator** para **nascimento**.  
  
4.  Salvar o DSL, clique em transformar todos os modelos e pressione F5.  
  
5.  Em um diagrama de modelo de exemplo, verifique se você pode agora clique as posições que você escolheu e digite os valores para eles. Além disso, quando você seleciona um **pessoa** forma, a janela Propriedades exibe as novas propriedades de nascimento e morte.  
  
6.  Em um arquivo. TT, você pode adicionar o código que obtém as propriedades de cada pessoa.  
  
 ![Diagrama de árvore de família, caixa de ferramentas e explorer](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>Definir novas Classes  
 Você pode adicionar classes de domínio e relações em um modelo. Por exemplo, você pode criar uma nova classe para representar cidades e uma nova relação para representar que uma pessoa que estiveram ativos em uma cidade.  
  
 Para tornar os diferentes tipos distintos em um diagrama de modelo, você pode mapear as classes de domínio para diferentes tipos de forma ou formas com cores e geometria diferente.  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>Para adicionar e exibe uma nova classe de domínio  
  
1.  Adicione uma classe de domínio e torná-lo um filho da raiz do modelo.  
  
    1.  No diagrama de definição de DSL, clique o **inserindo relação** ferramenta, clique na classe raiz **FamilyTreeModel**e, em seguida, clique em uma parte vazia do diagrama.  
  
         Uma nova classe de domínio é exibida, que está conectado ao FamilyTreeModel com um relacionamento de incorporação.  
  
         Defina seu nome, por exemplo **Cidade**.  
  
        > [!NOTE]
        >  Cada classe de domínio, exceto a raiz do modelo deve ser o destino de pelo menos um relacionamento de incorporação ou ele deve herdar de uma classe que é o destino de uma inserção. Por esse motivo, é conveniente com frequência criar uma classe de domínio usando a ferramenta de inserção de relação.  
  
    2.  Adicionar uma propriedade de domínio para a nova classe, por exemplo **nome**.  
  
2.  Adicione uma relação de referência entre pessoa e cidade.  
  
    1.  Clique o **relação de referência** ferramenta, clique em pessoa e, em seguida, clique em cidade.  
  
         ![Fragmento da definição de DSL: raiz da árvore de família](../modeling/media/familyt_root.png "FamilyT_Root")  
  
        > [!NOTE]
        >  Relações de referência representam referências cruzadas de uma parte da árvore modelo para outro.  
  
3.  Adicione uma forma para representar as cidades em diagramas de modelo.  
  
    1.  Arraste um **geometria forma** da caixa de ferramentas para o diagrama e renomeá-lo, por exemplo **TownShape**.  
  
    2.  Na janela Propriedades, defina os campos de aparência da nova forma, como cor de preenchimento e Geometry.  
  
    3.  Adicione um decorador para exibir o nome da cidade e renomeá-la NameDecorator. Defina sua propriedade de posição.  
  
4.  A classe de domínio de cidade são mapeados para o TownShape.  
  
    1.  Clique o **mapa de elemento de diagrama** ferramenta, clique na classe de domínio de cidade e, em seguida, a classe de forma TownShape.  
  
    2.  No **decorador mapas** guia do **DSL detalhes** janela com o conector de mapa selecionado, verifique NameDecorator e defina **propriedade Display** ao nome.  
  
5.  Crie um conector para exibir a relação entre a pessoa e cidades.  
  
    1.  Arraste um conector da caixa de ferramentas para o diagrama. Renomeie-o e definir suas propriedades de aparência.  
  
    2.  Use o **mapa de elemento de diagrama** ferramenta para vincular o novo conector para a relação entre a pessoa e cidade.  
  
         ![Definição de árvore com mapa de formas adicionado](../modeling/media/familyt_shapemap.png "FamilyT_ShapeMap")  
  
6.  Crie uma ferramenta de elemento para fazer uma cidade de novo.  
  
    1.  Em **DSL Explorer**, expanda **Editor** , em seguida, **guias da caixa de ferramentas**.  
  
    2.  Clique com botão direito  *\<seu DSL >* e, em seguida, clique em **adicionar nova ferramenta de elemento**.  
  
    3.  Definir o **nome** propriedade a nova ferramenta e defina seu **classe** propriedade cidade.  
  
    4.  Definir o **ícone caixa de ferramentas** propriedade. Clique em **[...]**  e no **nome de arquivo** , selecione um arquivo de ícone.  
  
7.  Crie uma ferramenta de conector para criar um link entre cidades e pessoas.  
  
    1.  Clique com botão direito  *\<seu DSL >* e, em seguida, clique em **adicionar nova ferramenta de conector**.  
  
    2.  Defina a propriedade de nome da nova ferramenta.  
  
    3.  No **ConnectionBuilder** propriedade, selecione o construtor que contém o nome da relação cidade da pessoa.  
  
    4.  Definir o **ícone caixa de ferramentas**.  
  
8.  Salvar a definição de DSL, clique em **transformar todos os modelos de**e, em seguida, pressione **F5**.  
  
9. Na instância experimental do Visual Studio, abra um arquivo de modelo de teste. Use as novas ferramentas para criar links entre cidades e pessoas e cidades. Observe que só é possível criar links entre os tipos de elemento corretos.  
  
10. Crie código que lista o município no qual reside cada pessoa. Modelos de texto são um dos locais onde você pode executar esse código. Por exemplo, você pode modificar o arquivo Sample.tt existente na solução de depuração para que ele contém o código a seguir:  
  
    ```  
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>  
    <#@ output extension=".txt" #>  
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>  
  
    <#  
      foreach (Person person in this.FamilyTreeModel.People)  
      {  
    #>  
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>  
  
    <#  
          foreach (Person child in person.Children)  
      {  
    #>  
                <#= child.Name #>  
    <#  
      }  
      }  
    #>  
  
    ```  
  
     Quando você salvar o arquivo *.tt, ele criará um arquivo da subsidiária que contém a lista de pessoas e suas residências. Para obter mais informações, consulte [código de geração de uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="validation-and-commands"></a>Comandos e validação  
 Você poderá desenvolver esse DSL ainda mais adicionando restrições de validação. Essas restrições são métodos que você pode definir, certifique-se de que o modelo está no estado correto. Por exemplo, você pode definir uma restrição para garantir que a data de nascimento do filho é posterior de seus pais. O recurso de validação exibirá um aviso se o usuário DSL tenta salvar um modelo que quebras de qualquer uma das restrições. Para obter mais informações, consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).  
  
 Você também pode definir os comandos de menu que o usuário pode invocar. Comandos podem modificar o modelo. Eles também podem interagir com outros modelos no Visual Studio e recursos externos. Para obter mais informações, consulte [como: modificar um comando de Menu padrão](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="deploying-the-dsl"></a>Implantando o DSL  
 Para permitir que outros usuários usar a linguagem específica de domínio, é possível distribuir um arquivo de extensão de Visual Studio (VSIX). Isso é criado quando você compila a solução DSL.  
  
 Localize o arquivo de .vsix na pasta bin de sua solução. Copie-o para o computador no qual você deseja instalá-lo. Nesse computador, clique duas vezes no arquivo VSIX. O DSL pode ser usado em todas as instâncias do Visual Studio no computador.  
  
 Você pode usar o mesmo procedimento para instalar o DSL em seu computador para que você não precisa usar a instância experimental do Visual Studio.  
  
 Para obter mais informações, consulte [implantar soluções de linguagem específica de domínio](../modeling/deploying-domain-specific-language-solutions.md).  
  
##  <a name="Reset"></a>Removendo DSLs Experimental antigo  
 Se você tiver criado DSLs experimentais que você não deseja mais, você poderá removê-los do seu computador, redefinindo a instância Experimental do Visual Studio.  
  
 Isso removerá do seu computador todas as DSLs experimentais e outras extensões experimentais do Visual Studio. Essas são extensões que foram executadas no modo de depuração.  
  
 Esse procedimento não remove DSLs ou outras extensões do Visual Studio que foram totalmente instaladas executando o arquivo VSIX.  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Para redefinir a instância Experimental do Visual Studio  
  
1.  Clique em **iniciar**, clique em **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**e, em seguida, **redefinição da Microsoft Instância do Visual Studio 2010 Experimental**.  
  
2.  Recompile qualquer DSLs experimentais ou outras extensões do Visual Studio experimentais que deseja usar.  
  
## <a name="see-also"></a>Consulte também

[Noções básicas sobre modelos, Classes e relacionamentos](../modeling/understanding-models-classes-and-relationships.md)   
[Como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md)

