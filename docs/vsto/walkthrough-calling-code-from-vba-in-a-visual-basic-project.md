---
title: 'Passo a passo: Chamando código do VBA em um projeto do Visual Basic | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: efb8f6c2759760fe2eb5c5d5ccf23e0942eac93a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-calling-code-from-vba-in-a-visual-basic-project"></a>Instruções passo a passo: chamando código de VBA em um projeto do Visual Basic
  Este passo a passo demonstra como chamar um método em uma personalização no nível do documento para o Microsoft Office Word no Visual Basic para o código do VBA no documento. O procedimento envolve três etapas básicas: adicionar um método para o `ThisDocument` classe de item de host, expor o método para o código do VBA e, em seguida, chame o método do código do VBA no documento.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Embora este passo a passo usa o Word especificamente, os conceitos demonstrados pelo passo a passo também se aplicam a projetos no nível de documento para Excel.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um documento que contém o código do VBA.  
  
-   Confiando o local do documento usando a Central de confiabilidade do Word.  
  
-   Adicionando um método para o `ThisDocument` classe de item de host.  
  
-   Expondo o método para o código do VBA.  
  
-   Chamando o método de código do VBA.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-a-document-that-contains-vba-code"></a>Criando um documento que contém o código do VBA  
 A primeira etapa é criar um documento habilitada para macro que contém uma macro VBA simples. O documento deve conter um projeto do VBA, antes de criar um projeto do Visual Studio que é baseado no documento. Caso contrário, o Visual Studio não pode modificar o projeto do VBA para habilitar o código do VBA chamar o assembly de personalização.  
  
 Se você já tiver um documento que contém o código do VBA que você deseja usar, você pode ignorar esta etapa.  
  
#### <a name="to-create-a-document-that-contains-vba-code"></a>Para criar um documento que contém o código do VBA  
  
1.  Inicie o Word.  
  
2.  Salvar o documento ativo como uma palavra **documento habilitado para macro (\*docm)** com o nome **DocumentWithVBA**. Salvá-lo em um local conveniente, como a área de trabalho.  
  
3.  Na faixa de opções, clique no **desenvolvedor** guia.  
  
    > [!NOTE]  
    >  Se o **desenvolvedor** guia não estiver visível, você deve primeiro mostrá-la. Para obter mais informações, consulte [como: Mostrar a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  No **código** de grupo, clique em **Visual Basic**.  
  
     Abre o Editor do Visual Basic.  
  
5.  No **projeto** janela, clique duas vezes em **ThisDocument**.  
  
     O arquivo de código para o `ThisDocument` objeto é aberta.  
  
6.  Adicione o seguinte código do VBA no arquivo de código. Esse código define uma função simples que não faz nada. O único propósito dessa função é garantir que existe um projeto do VBA no documento. Isso é necessário para etapas posteriores neste passo a passo.  
  
    ```  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Salve o documento e sair do Word.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 Agora você pode criar um projeto de nível de documento para Word, que usa o documento habilitada para macro criado anteriormente.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**. Se seu IDE está definido para usar configurações de desenvolvimento do Visual Basic, no **arquivo** menu, clique em **novo projeto**.  
  
3.  No painel de modelos, expanda **Visual Basic**e, em seguida, expanda **Office/SharePoint**.  
  
4.  Selecione o **suplementos do Office** nó.  
  
5.  Na lista de modelos de projeto, selecione o **documento do Word 2010** ou **documento do Word 2013** projeto.  
  
6.  No **nome** , digite **CallingCodeFromVBA**.  
  
7.  Clique em **OK**.  
  
     O **Visual Studio Tools para Office Project Wizard** é aberto.  
  
8.  Selecione **copiar um documento existente**e, no **caminho completo do documento existente** , especifique o local do **DocumentWithVBA** documento que você criou anteriormente . Se você estiver usando seu próprio documento habilitado para macros, especifique o local deste documento, em vez disso.  
  
9. Clique em **Finalizar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Abre o **DocumentWithVBA** de documento no designer e adiciona o **CallingCodeFromVBA** projeto **Gerenciador de soluções**.  
  
## <a name="trusting-the-location-of-the-document"></a>Confiando o local do documento  
 Antes de você pode expor o código em sua solução para o código do VBA no documento, você deve confiar VBA para executar no documento. Há várias maneiras de fazer isso. Para este passo a passo, confiar no local do documento no **Central de confiabilidade** no Word.  
  
#### <a name="to-trust-the-location-of-the-document"></a>Para confiar no local do documento  
  
1.  Inicie o Word.  
  
2.  Clique o **arquivo** guia.  
  
3.  Clique o **opções do Word** botão.  
  
4.  No painel de categorias, clique em **Central de confiabilidade**.  
  
5.  No painel de detalhes, clique em **definições**.  
  
6.  No painel de categorias, clique em **locais confiáveis**.  
  
7.  No painel de detalhes, clique em **adicionar novo local**.  
  
8.  No **local confiável do Microsoft Office** caixa de diálogo, navegue até a pasta que contém o **CallingCodeFromVBA** projeto.  
  
9. Selecione **subpastas deste local também são confiáveis**.  
  
10. No **local confiável do Microsoft Office** caixa de diálogo, clique em **Okey**.  
  
11. No **Central de confiabilidade** caixa de diálogo, clique em **Okey**.  
  
12. No **opções do Word** caixa de diálogo, clique em **Okey**.  
  
13. Saia do Word.  
  
## <a name="adding-a-method-to-the-thisdocument-class"></a>Adicionando um método à classe ThisDocument  
 Agora que o projeto do VBA estiver configurado, adicione um método para o `ThisDocument` classe de item que pode ser chamado de código VBA de host.  
  
#### <a name="to-add-a-method-to-the-thisdocument-class"></a>Para adicionar um método à classe ThisDocument  
  
1.  Em **Solution Explorer**, clique com botão direito **ThisDocument. vb**e, em seguida, clique em **Exibir código**.  
  
     O **ThisDocument. vb** arquivo é aberto no Editor de códigos.  
  
2.  Adicione o seguinte método à classe `ThisDocument`. Esse método cria uma tabela com duas linhas e duas colunas no início do documento. Os parâmetros especificam o texto que é exibido na primeira linha. Posteriormente neste passo a passo, você chamará esse método no código do VBA no documento.  
  
     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]  
  
3.  Compile o projeto.  
  
## <a name="exposing-the-method-to-vba-code"></a>Expondo o método para o código do VBA  
 Para expor o `CreateTable` método ao código do VBA no documento, defina o **EnableVbaCallers** propriedade para o `ThisDocument` item de host para **True**.  
  
#### <a name="to-expose-the-method-to-vba-code"></a>Para expor o método para o código do VBA  
  
1.  Em **Solution Explorer**, clique duas vezes em **ThisDocument. vb**.  
  
     O **DocumentWithVBA** arquivo é aberto no designer.  
  
2.  No **propriedades** janela, selecione o **EnableVbaCallers** propriedade e altere o valor para **True**.  
  
3.  Clique em **Okey** na mensagem que é exibida.  
  
4.  Compile o projeto.  
  
## <a name="calling-the-method-from-vba-code"></a>Chamando o método de código do VBA  
 Agora você pode chamar o `CreateTable` método do código do VBA no documento.  
  
> [!NOTE]  
>  Este passo a passo, você adicionará o código do VBA no documento durante a depuração do projeto. O código do VBA que você adicionar a este documento será substituído na próxima vez que você compilar o projeto, como Visual Studio substitui o documento na pasta de saída de compilação com uma cópia do documento da pasta de projeto principal. Se você deseja salvar o código do VBA, copie-o para o documento na pasta do projeto. Para obter mais informações, consulte [combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### <a name="to-call-the-method-from-vba-code"></a>Para chamar o método do código do VBA  
  
1.  Pressione F5 para executar o projeto.  
  
2.  No **desenvolvedor** guia o **código** de grupo, clique em **Visual Basic**.  
  
     Abre o Editor do Visual Basic.  
  
3.  Sobre o **inserir** menu, clique em **módulo**.  
  
4.  Adicione o seguinte código para o novo módulo.  
  
     Esse código chama o `CreateTable` método no assembly de personalização. A macro acessa esse método usando o `CallVSTOAssembly` propriedade o `ThisDocument` objeto. Essa propriedade foi gerada automaticamente quando você define o **EnableVbaCallers** propriedade anteriormente neste passo a passo.  
  
    ```  
    Sub CreateTable()  
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")  
    End Sub  
    ```  
  
5.  Pressione F5.  
  
6.  Verifique se uma nova tabela foi adicionada ao documento.  
  
7.  Saia do Word sem salvar as alterações.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre chamando código em soluções do Office por meio do VBA nestes tópicos:  
  
-   Chame o código em uma personalização do Visual c# do VBA. Esse processo é diferente do processo do Visual Basic. Para obter mais informações, consulte [passo a passo: chamando código de VBA em um Visual C&#35; projeto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
-   Chame o código em um suplemento do VSTO por meio do VBA. Para obter mais informações, consulte [passo a passo: chamando código em um suplemento do VSTO por meio do VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Consulte também  
 [Combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Personalizações no nível do documento da programação](../vsto/programming-document-level-customizations.md)   
 [Como: expor código para VBA em um projeto do Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Como: expor código para VBA em um Visual C&#35; projeto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Passo a passo: Chamando código do VBA em um Visual C&#35; projeto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)  
  
  