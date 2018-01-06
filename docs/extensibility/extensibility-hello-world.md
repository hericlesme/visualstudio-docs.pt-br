---
title: "Olá, mundo | Microsoft Docs"
ms.custom: 
ms.date: 07/10/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1b7d695f2211f01ce374ee41404d5ab49abde70a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-your-first-extension-hello-world"></a>Criando sua primeira extensão: Hello World

Este exemplo Hello World ensina a criar sua primeira extensão para o Visual Studio. Este tutorial mostra como adicionar um novo comando para o Visual Studio.

O processo, você aprenderá como:

* **[Criar um projeto de extensibilidade](#create-an-extensibility-project)**
* **[Adicionar um comando personalizado](#add-a-custom-command)**
* **[Modificar o código-fonte](#modify-the-source-code)**
* **[Executá-lo](#run-it)**

Neste exemplo, você usará o Visual C# para adicionar que um botão de menu personalizado chamado "Diga Olá, mundo!" que tem esta aparência:

![comando do Hello world](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, certifique-se de ter instalado o **desenvolvimento de extensão do Visual Studio** carga de trabalho que inclui o modelo VSIX que você precisa e código de exemplo.

Observação: Você pode usar qualquer versão do Visual Studio (Community, Professional ou Enterprise) para criar um projeto de extensibilidade do Visual Studio.

## <a name="create-an-extensibility-project"></a>Criar um projeto de extensibilidade

Etapa 1. Do **arquivo** menu, clique em **novo projeto**. Na parte inferior da tela, você pode inserir o nome do seu projeto.

Etapa 2. Do **modelos** menu, clique em **Visual C#**, clique em **extensibilidade**e, em seguida, clique em **projeto VSIX**.

![Novo projeto](media/hello-world-new-project.png)

Agora você verá a página de Introdução e alguns recursos de exemplo.

Se você precisar deixar este tutorial e voltar a ele, você pode encontrar seu novo projeto HelloWorld no **página inicial** no **recentes** seção.

## <a name="add-a-custom-command"></a>Adicionar um comando personalizado

Etapa 1. Se você selecionar o manifesto, você pode ver quais são as opções mutáveis de instância, metadados, descrição e versão.

Etapa 2. Clique com botão direito no projeto (não a solução). No menu de contexto, clique em **adicionar**e, em seguida, clique em **controle de usuário**.

Etapa 3. Volte para o **extensibilidade** seção e, em seguida, clique em **comando personalizado**.

Etapa 4. No **nome** campo na parte inferior, dê a ele um nome, por exemplo Command.cs.

![comando personalizado](media/hello-world-custom-command.png)

Novo comando será listado no **Solution Explorer** sob o **recursos** ramificação. Isso também é onde você encontrará outros arquivos relacionados ao seu comando, como os arquivos PNG e ICO se você deseja modificar a imagem.

## <a name="modify-the-source-code"></a>Modificar o código-fonte

Neste ponto, o botão Adicionar é muito genérico. Você precisará modificar o arquivo VSCT e o arquivo de CS, se você quiser fazer alterações.

* O arquivo VSCT é onde você pode renomear os comandos, bem como definir onde entram no sistema de linha de comando do Visual Studio. Conforme você explora o arquivo VSCT, você observará muito código comentado que explica o que cada seção dos controles do código.

* O arquivo de CS é onde você pode definir ações, como o manipulador de cliques.

Etapa 1. Em **Solution Explorer**, localizar o arquivo VSCT para seu novo comando. Nesse caso, ele será chamado CommandPackage.vsct.

![comando pacote vsct](media/hello-world-command-package-vsct.png)

Etapa 2. Alterar o `ButtonText` parâmetro para "Diga Olá, mundo!"

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Etapa 3. Volte para **Solution Explorer** e localize o arquivo Command.cs. Alterar a cadeia de caracteres `message` para o comando `string.Format(..)` para "Hello World!"

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Certifique-se de salvar suas alterações para cada arquivo.

## <a name="run-it"></a>Executá-lo

Agora você pode executar o código-fonte na instância Experimental do Visual Studio.

Etapa 1. Clique em **iniciar** na barra de ferramentas. Isso criará seu projeto e iniciar o depurador, iniciando uma nova instância do Visual Studio chamado o **instância Experimental**.

Você verá as palavras "Instância Experimental" na barra de título do Visual Studio.

![barra de título da instância experimental](media/hello-world-exp-instance.png)

Etapa 2. No **ferramentas** menu o **instância Experimental**, clique em **diga Olá, mundo!**.

![resultado final](media/hello-world-final-result.png)

Você deve ver a saída do comando personalizado novo, neste caso, a caixa de diálogo no centro da tela que lhe dá o "Hello World!" .

## <a name="next-steps"></a>Próximas etapas

Agora que você conhece os fundamentos de trabalhar com a extensibilidade do Visual Studio, aqui é onde você pode saber mais:

* [Começando a desenvolver extensões do Visual Studio](starting-to-develop-visual-studio-extensions.md) -exemplos, tutoriais. e publicar sua extensão.
* [Novidades no SDK do Visual Studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) -novos recursos de extensibilidade do Visual Studio de 2017
* [Dentro do Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -saber os detalhes de extensibilidade do Visual Studio