---
title: Criar uma categoria de configurações | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22a625466dd8a94ba1dbe67ef6f05bec68954d2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-settings-category"></a>Criar uma categoria de configurações
Neste passo a passo, você cria uma categoria de configurações do Visual Studio e usá-lo para salvar os valores e restaurar os valores de um arquivo de configurações. Uma categoria de configuração é um grupo de propriedades relacionadas que aparecem como um "ponto de configurações personalizadas;" ou seja, como uma caixa de seleção de **importar e exporta configurações** assistente. (Você pode encontrar o **ferramentas** menu.) As configurações são salvas ou restauradas como uma categoria e configurações individuais não são exibidas no assistente. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Criar uma categoria de configurações derivando do <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.  
  
 Para iniciar esta explicação passo a passo, você deve primeiro concluir a primeira seção do [criando uma página de opções](../extensibility/creating-an-options-page.md). A grade de propriedades Opções resultante permite examinar e alterar as propriedades na categoria. Depois de salvar a categoria de propriedade em um arquivo de configurações, você pode examinar o arquivo para ver como os valores de propriedade são armazenados.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Criar uma categoria de configurações  
 Nesta seção, você pode usar um ponto de configurações personalizadas para salvar e restaurar os valores da categoria de configurações.  
  
#### <a name="to-create-a-settings-category"></a>Para criar uma categoria de configurações  
  
1.  Concluir o [criando uma página de opções](../extensibility/creating-an-options-page.md).  
  
2.  Abra o arquivo VSPackage.resx e adicione estes recursos de cadeia de caracteres de três:  
  
    |Nome|Valor|  
    |----------|-----------|  
    |106|Minha categoria|  
    |107|Minhas configurações|  
    |108|OptionInteger e OptionFloat|  
  
     Isso cria recursos que a categoria 'Meus categoria' nome, o objeto "Minhas configurações" e a descrição da categoria "OptionInteger e OptionFloat".  
  
    > [!NOTE]
    >  Esses três, apenas o nome da categoria não aparecem no Assistente para importar e exportar configurações.  
  
3.  Em MyToolsOptionsPackage.cs, adicione um `float` propriedade denominada `OptionFloat` para o `OptionPageGrid` de classe, conforme mostrado no exemplo a seguir.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  O `OptionPageGrid` categoria chamada "My Category" agora consiste em duas propriedades, `OptionInteger` e `OptionFloat`.  
  
4.  Adicionar um <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> para o `MyToolsOptionsPackage` classe e dê a ele o CategoryName "My Category", dê a ele o ObjectName "Minhas configurações" e defina isToolsOptionPage como true. Defina o categoryResourceID, objectNameResourceID e DescriptionResourceID para o recurso de cadeia de caracteres correspondente, que as IDs criadas anteriormente.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Compile o projeto e comece a depuração. A instância experimental você verá que **minha página da grade** agora tem valores flutuantes e inteiros.  
  
## <a name="examining-the-settings-file"></a>Examinando o arquivo de configurações  
 Nesta seção, você pode exportar os valores de categoria de propriedade para um arquivo de configurações. Examine o arquivo e, em seguida, importe os valores novamente para a categoria de propriedade.  
  
1.  Inicie o projeto no modo de depuração pressionando F5. Isso inicia a instância experimental.  
  
2.  Abra o **Ferramentas / opções** caixa de diálogo.  
  
3.  Na exibição de árvore no painel esquerdo, expanda **Categoria Meus** e, em seguida, clique em **minha página da grade**.  
  
4.  Alterar o valor de **OptionFloat** para 3.1416 e **OptionInteger** a 12. Clique em **OK**.  
  
5.  Sobre o **ferramentas** menu, clique em **importar e exportar configurações**.  
  
     O **importar e exportar configurações** assistente é exibido.  
  
6.  Certifique-se de **configurações de ambiente selecionadas de exportação** está selecionado e, em seguida, clique em **próximo**.  
  
     O **escolher configurações de exportação** página será exibida.  
  
7.  Clique em **minhas configurações**.  
  
     O **descrição** alterações **OptionInteger e OptionFloat**.  
  
8.  Verifique se **minhas configurações** é a única categoria selecionada e, em seguida, clique em **próximo**.  
  
     O **nome do arquivo de configurações** página será exibida.  
  
9. Nomeie o novo arquivo de configurações `MySettings.vssettings` e salvá-lo em um diretório apropriado. Clique em **Finalizar**.  
  
     O **Exportação concluída** página relatórios de que suas configurações foram exportadas com êxito.  
  
10. Sobre o **arquivo** , aponte para **abrir**e, em seguida, clique em **arquivo**. Localize `MySettings.vssettings` e abri-lo.  
  
     Você pode encontrar a categoria de propriedade que você exportou na seção a seguir do arquivo (seus GUIDs serão diferentes).  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     Observe que o nome da categoria inteira é formado pela adição de um sublinhado para o nome da categoria seguido do nome do objeto. OptionFloat e OptionInteger são exibidos na categoria, junto com seus valores exportados.  
  
11. Feche o arquivo de configurações sem alterá-lo.  
  
12. No **ferramentas** menu, clique em **opções**, expanda **Categoria Meus**, clique em **minha página da grade** e, em seguida, altere o valor de  **OptionFloat** 1.0 e **OptionInteger** como 1. Clique em **OK**.  
  
13. Sobre o **ferramentas** menu, clique em **importar e exportar configurações**, selecione **configurações de ambiente selecionadas de importação**e, em seguida, clique em **próximo**.  
  
     O **salvar configurações atuais** página será exibida.  
  
14. Selecione **não, apenas importe as novas configurações** e, em seguida, clique em **próximo**.  
  
     O **escolha uma coleção de configurações a importar** página será exibida.  
  
15. Selecione o `MySettings.vssettings` arquivo o **minhas configurações** nó da exibição de árvore. Se o arquivo não aparecem na exibição de árvore, clique em **procurar** e localizá-lo. Clique em **Avançar**.  
  
     O **escolher configurações a importar** caixa de diálogo é exibida.  
  
16. Verifique se **minhas configurações** está selecionado e, em seguida, clique em **concluir**. Quando o **importação completa** página aparece, clique em **fechar**.  
  
17. No **ferramentas** menu, clique em **opções**, expanda **Categoria Meus**, clique em **minha página da grade** e verifique se tem os valores de categoria de propriedade foi restaurado.