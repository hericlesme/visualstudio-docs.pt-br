---
title: "Passo a passo: Chamando código do VBA em um projeto do Visual c# | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 109ae2e89cf30078c910ff313ea203c576906037
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-calling-code-from-vba-in-a-visual-c-project"></a>Instruções passo a passo: chamando código de VBA em um projeto do Visual C#
  Este passo a passo demonstra como chamar um método em uma personalização de nível de documento do Microsoft Office Excel do Visual Basic para código Applications (VBA) na pasta de trabalho. O procedimento envolve três etapas básicas: adicionar um método para o `Sheet1` classe de item de host, expor o método para o código do VBA na pasta de trabalho e, em seguida, chame o método do código do VBA na pasta de trabalho.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Embora este passo a passo usa o Excel especificamente, os conceitos demonstrados pelo passo a passo sejam aplicam a projetos de nível de documento para Word.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando uma pasta de trabalho que contém o código do VBA.  
  
-   Confiando o local da pasta de trabalho usando a Central de confiabilidade no Excel.  
  
-   Adicionando um método para o `Sheet1` classe de item de host.  
  
-   Extraindo uma interface para o `Sheet1` classe de item de host.  
  
-   Expondo o método para o código do VBA.  
  
-   Chamando o método de código do VBA.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-a-workbook-that-contains-vba-code"></a>Criando uma pasta de trabalho que contém o código do VBA  
 A primeira etapa é criar uma pasta de trabalho habilitada para macro que contém uma macro VBA simples. Antes de você pode expor o código em uma personalização para VBA, a pasta de trabalho já deve conter o código do VBA. Caso contrário, o Visual Studio não pode modificar o projeto do VBA para habilitar o código do VBA chamar o assembly de personalização.  
  
 Se você já tiver uma pasta de trabalho que contém o código do VBA que você deseja usar, você pode ignorar esta etapa.  
  
#### <a name="to-create-a-workbook-that-contains-vba-code"></a>Para criar uma pasta de trabalho que contém o código do VBA  
  
1.  Inicie o Excel.  
  
2.  Salvar o documento ativo como um **pasta de trabalho (\*. xlsm)** com o nome **WorkbookWithVBA**. Salvá-lo em um local conveniente, como a área de trabalho.  
  
3.  Na faixa de opções, clique no **desenvolvedor** guia.  
  
    > [!NOTE]  
    >  Se o **desenvolvedor** guia não estiver visível, você deve primeiro mostrá-la. Para obter mais informações, consulte [como: Mostrar a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  No **código** de grupo, clique em **Visual Basic**.  
  
     Abre o Editor do Visual Basic.  
  
5.  No **projeto** janela, clique duas vezes em **ThisWorkbook**.  
  
     O arquivo de código para o `ThisWorkbook` objeto é aberta.  
  
6.  Adicione o seguinte código do VBA no arquivo de código. Esse código define uma função simples que não faz nada. O único propósito dessa função é garantir que um projeto VBA existe na pasta de trabalho. Isso é necessário para etapas posteriores neste passo a passo.  
  
    ```  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Salve o documento e saia do Excel.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 Agora você pode criar um projeto de nível de documento para Excel que usa a pasta de trabalho habilitada para macro criado anteriormente.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel de modelos, expanda **Visual C#**e, em seguida, expanda **Office/SharePoint**.  
  
4.  Selecione o **suplementos do Office** nó.  
  
5.  Na lista de modelos de projeto, selecione o **pasta de trabalho do Excel 2010** ou **pasta de trabalho do Excel 2013** projeto.  
  
6.  No **nome** , digite **CallingCodeFromVBA**.  
  
7.  Clique em **OK**.  
  
     O **Visual Studio Tools para Office Project Wizard** é aberto.  
  
8.  Selecione **copiar um documento existente**e, no **caminho completo do documento existente** , especifique o local do **WorkbookWithVBA** pasta de trabalho que você criou anteriormente . Se você estiver usando sua própria pasta de trabalho habilitada para macro, especifica o local da pasta de trabalho.  
  
9. Clique em **Finalizar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Abre o **WorkbookWithVBA** pasta de trabalho no designer e adiciona o **CallingCodeFromVBA** projeto **Gerenciador de soluções**.  
  
## <a name="trusting-the-location-of-the-workbook"></a>Confiando o local da pasta de trabalho  
 Antes de você pode expor o código em sua solução para o código do VBA na pasta de trabalho, você deve confiar VBA na pasta de trabalho para executar. Há várias maneiras de fazer isso. Neste passo a passo, você irá realizar essa tarefa confiar no local da pasta de trabalho no **Central de confiabilidade** no Excel.  
  
#### <a name="to-trust-the-location-of-the-workbook"></a>Para confiar no local da pasta de trabalho  
  
1.  Inicie o Excel.  
  
2.  Clique o **arquivo** guia.  
  
3.  Clique o **opções do Excel** botão.  
  
4.  No painel de categorias, clique em **Central de confiabilidade**.  
  
5.  No painel de detalhes, clique em **definições**.  
  
6.  No painel de categorias, clique em **locais confiáveis**.  
  
7.  No painel de detalhes, clique em **adicionar novo local**.  
  
8.  No **local confiável do Microsoft Office** caixa de diálogo, navegue até a pasta que contém o **CallingCodeFromVBA** projeto.  
  
9. Selecione **subpastas deste local também são confiáveis**.  
  
10. No **local confiável do Microsoft Office** caixa de diálogo, clique em **Okey**.  
  
11. No **Central de confiabilidade** caixa de diálogo, clique em **Okey**.  
  
12. No **opções do Excel** caixa de diálogo, clique em **Okey**.  
  
13. Saída **Excel**.  
  
## <a name="adding-a-method-to-the-sheet1-class"></a>Adicionando um método à classe Sheet1  
 Agora que o projeto do VBA estiver configurado, adicione um método público para o `Sheet1` classe de item que pode ser chamado de código VBA de host.  
  
#### <a name="to-add-a-method-to-the-sheet1-class"></a>Para adicionar um método à classe Sheet1  
  
1.  Em **Solution Explorer**, clique com botão direito **Sheet1.cs**e, em seguida, clique em **Exibir código**.  
  
     O **Sheet1.cs** arquivo é aberto no Editor de códigos.  
  
2.  Adicione o seguinte código para o `Sheet1` classe. O `CreateVstoNamedRange` método cria um novo <xref:Microsoft.Office.Tools.Excel.NamedRange> objeto no intervalo especificado. Esse método cria um manipulador de eventos para o <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> evento o <xref:Microsoft.Office.Tools.Excel.NamedRange>. Posteriormente neste passo a passo, você chamará o `CreateVstoNamedRange` método do código do VBA no documento.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]  
  
3.  Adicione o seguinte método à classe `Sheet1`. Esse método substitui o <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> método para retornar a instância atual do `Sheet1` classe.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]  
  
4.  Aplicar os seguintes atributos antes da primeira linha do `Sheet1` declaração de classe. Esses atributos tornar visível a classe COM, mas sem gerar uma interface de classe.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]  
  
## <a name="extracting-an-interface-for-the-sheet1-class"></a>Extraindo uma Interface para a classe Sheet1  
 Antes de você pode expor o `CreateVstoNamedRange` método código VBA, você deve criar uma interface pública que define este método e deve expor essa interface a COM.  
  
#### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Para extrair uma interface para a classe Sheet1  
  
1.  No **Sheet1.cs** arquivo de código, clique em qualquer lugar do `Sheet1` classe.  
  
2.  Sobre o **refatorar** menu, clique em **extrair Interface**.  
  
3.  No **extrair Interface** na caixa de **selecionar membros públicos para formar interface** caixa, clique na entrada para o `CreateVstoNamedRange` método.  
  
4.  Clique em **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]gera uma nova interface chamada `ISheet1`, e ela modifica a definição do `Sheet1` de classe para que ele implementa o `ISheet1` interface. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]também abre o **ISheet1.cs** arquivo no Editor de códigos.  
  
5.  No **ISheet1.cs** de arquivo, substitua o `ISheet1` interface declaração com o código a seguir. Este código faz o `ISheet1` interface pública e ela se aplica a <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo para tornar a interface visível para COM.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]  
  
6.  Compile o projeto.  
  
## <a name="exposing-the-method-to-vba-code"></a>Expondo o método para o código do VBA  
 Para expor o `CreateVstoNamedRange` método ao código do VBA na pasta de trabalho, defina o **ReferenceAssemblyFromVbaProject** propriedade para o `Sheet1` item de host para **True**.  
  
#### <a name="to-expose-the-method-to-vba-code"></a>Para expor o método para o código do VBA  
  
1.  Em **Solution Explorer**, clique duas vezes em **Sheet1.cs**.  
  
     O **WorkbookWithVBA** arquivo é aberto no designer, Sheet1 visível.  
  
2.  No **propriedades** janela, selecione o **ReferenceAssemblyFromVbaProject** propriedade e altere o valor para **True**.  
  
3.  Clique em **Okey** na mensagem que é exibida.  
  
4.  Compile o projeto.  
  
## <a name="calling-the-method-from-vba-code"></a>Chamando o método de código do VBA  
 Agora você pode chamar o `CreateVstoNamedRange` método do código do VBA na pasta de trabalho.  
  
> [!NOTE]  
>  Este passo a passo, você adicionará código VBA para a pasta de trabalho durante a depuração do projeto. O código do VBA que você adicionar a este documento será substituído na próxima vez que você compilar o projeto, como Visual Studio substitui o documento na pasta de saída de compilação com uma cópia do documento da pasta de projeto principal. Se você deseja salvar o código do VBA, copie-o para o documento na pasta do projeto. Para obter mais informações, consulte [combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### <a name="to-call-the-method-from-vba-code"></a>Para chamar o método do código do VBA  
  
1.  Pressione F5 para executar o projeto.  
  
2.  No **desenvolvedor** guia o **código** de grupo, clique em **Visual Basic**.  
  
     Abre o Editor do Visual Basic.  
  
3.  Sobre o **inserir** menu, clique em **módulo**.  
  
4.  Adicione o seguinte código para o novo módulo.  
  
     Esse código chama o `CreateTable` método no assembly de personalização. A macro acessa esse método usando global `GetManagedClass` método para acessar o `Sheet1` classe de item que é exposto ao código do VBA de host. O `GetManagedClass` método foi gerado automaticamente quando você define o **ReferenceAssemblyFromVbaProject** propriedade anteriormente neste passo a passo.  
  
    ```  
    Sub CallVSTOMethod()  
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1  
        Set VSTOSheet1 = GetManagedClass(Sheet1)  
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")  
    End Sub  
    ```  
  
5.  Pressione F5.  
  
6.  Na pasta de trabalho aberta, clique na célula **A1** na **Planilha1**. Verifique se a caixa de mensagem aparece.  
  
7.  Saia do Excel sem salvar as alterações.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre chamando código em soluções do Office por meio do VBA nestes tópicos:  
  
-   Chame o código em um item de host em uma personalização do Visual Basic do VBA. Esse processo é diferente do processo do Visual c#. Para obter mais informações, consulte [passo a passo: chamando código de VBA em um projeto do Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  
  
-   Chame o código em um suplemento do VSTO por meio do VBA. Para obter mais informações, consulte [passo a passo: chamando código em um suplemento do VSTO por meio do VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Consulte também  
 [Combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Personalizações no nível do documento da programação](../vsto/programming-document-level-customizations.md)   
 [Como: expor código para VBA em um projeto do Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Como: expor código para VBA em um Visual C &#35; Projeto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Instruções passo a passo: chamando o código pelo VBA em um projeto do Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
  