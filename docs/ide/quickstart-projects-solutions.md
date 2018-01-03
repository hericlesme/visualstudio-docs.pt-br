---
title: "Introdução aos projetos e às soluções no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 12/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b757178f29439f162df9e8844ae65ed8df642bb5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-projects-and-solutions"></a>Guia de início rápido: projetos e soluções

Neste guia de início rápido de 10 minutos, vamos explorar o que significa criar uma solução e um projeto no Visual Studio. Vamos examinar as propriedades de um projeto e alguns dos arquivos que ele pode conter. Também vamos criar uma referência a um segundo projeto.

> [!TIP]
> Desenvolveremos uma solução e um projeto do zero neste guia de início rápido, como um exercício educacional para compreendermos o conceito de um projeto. Em seu uso geral do Visual Studio, você provavelmente utilizará os vários modelos de projeto que ele oferece quando estiver criando um novo projeto.

> [!NOTE]
> As soluções e os projetos não são necessários para desenvolver aplicativos no Visual Studio. Você também pode apenas abrir uma pasta que contenha o código e começar a codificar, compilar e depurar. Por exemplo, se você clonar um repositório do GitHub, ele poderá não conter projetos e soluções do Visual Studio. Para obter mais informações, consulte [Desenvolver código no Visual Studio sem projetos nem soluções](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Soluções

As soluções são contêineres usados pelo Visual Studio para organizar um ou mais projetos relacionados. Quando você abre uma solução no Visual Studio, ele automaticamente carrega todos os projetos que contém.

### <a name="create-a-solution"></a>Criar uma solução

Vamos iniciar nossa exploração criando uma solução vazia. Depois de se familiarizar com o Visual Studio, você provavelmente não vai se pegar criando soluções vazias com muita frequência. Quando você cria um novo projeto no Visual Studio, ele desenvolverá automaticamente uma solução para hospedar o projeto, se não houver uma solução já aberta.

1. Inicie o Visual Studio.

   O Visual Studio é aberto e você provavelmente verá a **Página Inicial** ocupando a maior parte do espaço da janela.

1. Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto...**

   A caixa de diálogo **Novo Projeto** é aberta.

1. No painel esquerdo, expanda a opção **Outros Tipos de Projetos** e, então, selecione **Soluções do Visual Studio**. No painel central, escolha **Solução em Branco**. Nomeie a solução como “QuickSolution” e, em seguida, selecione **OK**.

   ![Modelo de solução em branco](media/quickstart-projects-new-solution.png)

   A **Página Inicial** é fechada e uma solução aparece no **Gerenciador de Soluções** à direita da janela do Visual Studio. Você provavelmente usará o **Gerenciador de Soluções** muitas vezes para navegar pelo conteúdo de seus projetos.

### <a name="add-a-project"></a>Adicionar um projeto

Agora vamos adicionar nosso primeiro projeto à solução. Vamos começar com um projeto vazio e adicionar os itens necessários ao projeto.

1. Ao clicar com o botão direito do mouse ou no menu de contexto da **Solução ‘QuickSolution’** do **Gerenciador de Soluções**, escolha **Adicionar** > **Novo Projeto...**

   A caixa de diálogo **Adicionar Novo Projeto** é aberta.

1. No painel esquerdo, expanda a opção **Visual C#** e escolha **Área de Trabalho Clássica do Windows**. Em seguida, no painel central, selecione **Projeto Vazio (.NET Framework)**. Nomeie o projeto como “QuickDate” e, então, selecione o botão **OK**.

   Um projeto chamado “QuickDate” aparecerá abaixo da solução no **Gerenciador de Soluções**. Atualmente, ele contém um único arquivo chamado **App.config**.

   > [!NOTE]
   > Se você não vir a opção **Visual C#** no painel esquerdo da caixa de diálogo, será necessário instalar a carga de trabalho **Desenvolvimento de área de trabalho do .NET**. Uma maneira fácil de fazer isso é clicar no link **Abrir Instalador do Visual Studio** na parte inferior do painel esquerdo. O **Instalador do Visual Studio** é aberto e, daí, você pode escolher a carga de trabalho correta e, em seguida, o botão **Modificar**.

   ![Abrir o link do Instalador do Visual Studio](media/quickstart-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>Adicionar um item ao projeto

Temos um projeto vazio&mdash;vamos adicionar um arquivo de código.

1. Ao clicar com o botão direito do mouse ou no menu de contexto **QuickDate** do **Gerenciador de Soluções**, selecione **Adicionar** > **Novo Item...**.

   A caixa de diálogo **Adicionar Novo Item** é aberta.

1. Expanda a opção **Itens do Visual C#** e, em seguida, escolha **Código**. No painel central, selecione **Classe**. Nomeie o arquivo como “Calendar” e, então, escolha o botão **Adicionar**.

   Um arquivo chamado “Calendar.cs” é adicionado ao projeto. O **.cs** no final é a extensão de arquivo que é fornecida aos arquivos de código C#. O arquivo é exibido na hierarquia do projeto visual no **Gerenciador de Soluções** e seu conteúdo é aberto no editor.

1. Substitua o conteúdo do arquivo **Calendar.cs** pelo código a seguir.

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   Você não precisa entender o que o código faz, mas se desejar, você pode executar o programa e ver que ele imprime a data de hoje na janela do console.

## <a name="add-a-second-project"></a>Adicionar um segundo projeto

É comum que as soluções contenham mais de um projeto e que, geralmente, esses projetos façam referência uns aos outros. Alguns projetos em uma solução podem ser bibliotecas de classes, alguns aplicativos executáveis e outros podem ser projetos de teste de unidade ou sites.

Vamos adicionar um projeto de teste de unidade em nossa solução. Desta vez, vamos começar de um modelo de projeto. Portanto, não precisamos adicionar um arquivo de código extra no projeto.

1. Ao clicar com o botão direito do mouse ou no menu de contexto da **Solução ‘QuickSolution’** do **Gerenciador de Soluções**, escolha **Adicionar** > **Novo Projeto...**

   A caixa de diálogo **Adicionar Novo Projeto** é aberta.

1. No painel esquerdo, expanda a opção **Visual Basic** e escolha a categoria **Teste**. No painel central, selecione **Projeto de Teste de Unidade (.NET Framework)**. Nomeie o projeto como “QuickTest” e, então, escolha o botão **OK**.

   Um segundo projeto é adicionado ao **Gerenciador de Soluções** e um arquivo chamado **UnitTest1.vb** é aberto no editor. O **.vb** é a extensão de arquivo que é fornecida aos arquivos de código do Visual Basic.

   ![Gerenciador de Soluções com dois projetos](media/quickstart-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>Adicionar uma referência ao projeto

Vamos usar o novo projeto de teste de unidade para testar nosso método no projeto **QuickDate**. Portanto, precisamos adicionar uma referência a esse projeto. Isso cria uma dependência de build entre os dois projetos, o que significa que o **QuickDate** será compilado antes do **QuickTest** quando a solução for compilada.

1. Escolha o nó **Referências** no projeto **QuickTest** e, ao clicar com o botão direito do mouse ou no menu de contexto, escolha **Adicionar Referência...**

   ![Adicionar menu de referência](media/quickstart-projects-add-reference.png)

   A caixa de diálogo **Gerenciador de Referências** é aberta.

1. No painel esquerdo, expanda **Projetos** e escolha **Solução**. No painel central, escolha a caixa de seleção ao lado de **QuickDate** e, em seguida, escolha o botão **OK**.

   Uma referência ao projeto **QuickDate** será adicionada.

## <a name="add-test-code"></a>Adicionar código de teste

1. Agora vamos adicionar o código de teste para o arquivo de código do Visual Basic. Substitua o conteúdo do **UnitTest1.vb** pelo seguinte código.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Você verá uma linha sinuosa vermelha em alguns dos códigos. Nós corrigiremos esse erro ao tornar o projeto de teste um [assembly amigável](/dotnet/csharp/programming-guide/concepts/assemblies-gac/friend-assemblies) para o projeto **QuickDate**.

1. De volta ao projeto **QuickDate**, abra o arquivo **Calendar.cs**, se ele já não estiver aberto e adicione a seguinte instrução de uso e o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para resolver o erro no projeto de teste.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   O arquivo de código deve ter este aspecto.

   ![Código CSharp](media/quickstart-projects-cs-code.png)

## <a name="project-properties"></a>Propriedades de projeto

A linha no arquivo do código C# que contém o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> faz referência ao nome do assembly do projeto **QuickTest**. O nome do assembly pode não ser sempre o mesmo que o nome do projeto. Para localizar o nome do assembly de um projeto, abra as propriedades do projeto.

1. No **Gerenciador de Soluções**, selecione o projeto **QuickTest**. Ao clicar com o botão direito do mouse ou no menu de contexto, selecione **Propriedades** ou pressione **Alt**+**Enter**.

   As páginas de propriedades do projeto são abertas na guia **Aplicativo**. Observe que o nome do assembly do projeto **QuickTest** é, de fato, “QuickTest”. Se você quisesse alterá-lo, este é o local em que o modificaria. Então, no momento em que você compilasse o projeto de teste, o nome do arquivo executável resultante seria alterado de **QuickTest.exe** para o que você tivesse escolhido.

   ![Propriedades de projeto](media/quickstart-projects-properties.png)

1. Explore algumas das outras guias das páginas de propriedades do projeto, como **Compilar** e **Configurações**. Dependendo do tipo de projeto, estas guias serão diferentes.

## <a name="next-steps"></a>Próximas etapas

Se você quiser verificar se seu teste de unidade está funcionando, selecione **Teste** > **Executar** > **Todos os Testes** na barra de menus. Uma janela chamada **Gerenciador de Testes** será aberta e você verá que o teste **TestGetCurrentDate** será aprovado.

Parabéns por concluir este guia de início rápido! Logo depois, talvez você queira explorar alguns dos outros guias de início rápido do Visual Studio ou saber mais sobre a [criação de projetos e de soluções](../ide/creating-solutions-and-projects.md).

## <a name="see-also"></a>Consulte também

[Início rápido: introdução ao IDE do Visual Studio](../ide/quickstart-ide-orientation.md)  
[Início rápido: personalizar o Editor e o IDE do Visual Studio](../ide/quickstart-personalize-the-ide.md)  
[Guia de início rápido: codificação no editor](../ide/quickstart-editor.md)  
[Gerenciando propriedades do projeto e da solução](../ide/managing-project-and-solution-properties.md)  
[Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)  
[Desenvolver código no Visual Studio sem projetos ou soluções](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)  
[Visão geral do IDE do Visual Studio](../ide/visual-studio-ide.md)
