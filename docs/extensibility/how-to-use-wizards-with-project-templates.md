---
title: 'Como: usar assistentes com modelos de projeto | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d29d2a1313bdb4e8a5e8654068984893578af4a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136088"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Como usar assistentes com modelos do projeto
O Visual Studio fornece o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface que, quando implementada, permite que você execute o código personalizado quando um usuário cria um projeto de um modelo.  
  
 Personalização do modelo de projeto pode ser usada para exibir a interface do usuário personalizada que coleta a entrada do usuário para personalizar o modelo, adicione arquivos adicionais para o modelo, ou qualquer outra ação permitida em um projeto.  
  
 O <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> métodos de interface são chamados em vários momentos enquanto o projeto está sendo criado, começando assim que um usuário clica em **Okey** no **novo projeto** caixa de diálogo. Cada método da interface é denominado para descrever o ponto no qual ele é chamado. Por exemplo, o Visual Studio chama <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> imediatamente no início da criação do projeto, tornando-um bom local para escrever código personalizado para coletar a entrada do usuário.  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>Criando um projeto de modelo de projeto com um projeto do VSIX  
 Começar a criar um modelo personalizado com o projeto modelo projeto., que faz parte do SDK do Visual Studio. Neste procedimento, usaremos um projeto de modelo de projeto c#, mas também há um projeto de modelo de projeto do Visual Basic. Em seguida, você adicionar um projeto do VSIX para a solução que contém o projeto de modelo de projeto.  
  
1.  Criar um projeto de modelo de projeto c# (no Visual Studio, **arquivo > Novo > projeto > Visual C# > extensibilidade > modelo de projeto c#**). Nomeie- **MyProjectTemplate**.  
  
    > [!NOTE]
    >  Você pode ser solicitado a instalar o SDK do Visual Studio. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Adicionar um novo projeto do VSIX (**arquivo > Novo > projeto > Visual C# > extensibilidade > projeto VSIX**) na mesma solução que o projeto de modelo de projeto (no **Solution Explorer**, selecione o nó da solução, o botão direito do mouse e selecione **Adicionar > Novo projeto**). Nomeie-o **MyProjectWizard.**  
  
3.  Defina o projeto do VSIX como o projeto de inicialização. No **Solution Explorer**, selecione o nó do projeto VSIX, com o botão direito e selecione **definir como projeto de inicialização**.  
  
4.  Adicione o projeto de modelo como um ativo do projeto VSIX. No **Solution Explorer**, sob o nó do projeto VSIX, localizar o **source.extension.vsixmanifest** arquivo. Clique duas vezes nele para abri-lo no editor de manifesto.  
  
5.  No editor de manifesto, selecione o **ativos** guia no lado esquerdo da janela.  
  
6.  No **ativos** guia, selecione **novo**. No **adicionar novo ativo** janela para o campo de tipo, selecione **Microsoft.VisualStudio.ProjectTemplate**. No **fonte** campo, selecione **um projeto na solução atual**. No **projeto** campo, selecione **MyProjectTemplate**. Clique em **OK**.  
  
7.  Compile a solução e inicie a depuração. Uma segunda instância do Visual Studio é exibida. (Isso pode levar alguns minutos.)  
  
8.  Na segunda instância do Visual Studio, tente criar um novo projeto com o novo modelo. (**Arquivo > Novo > projeto > Visual C# > modelo MyProject**). O novo projeto deve aparecer com uma classe chamada **Class1**. Você criou um modelo de projeto personalizado! Pare a depuração agora.  
  
## <a name="creating-a-custom-template-wizard"></a>Criando um Assistente de modelo personalizado  
 Este tópico mostra como criar um assistente personalizado que abre um formulário do Windows antes do projeto é criado. O formulário permite que os usuários adicionar um valor de parâmetro personalizado que é adicionado ao código-fonte durante a criação do projeto.  
  
1.  Configure o projeto do VSIX para permitir a criação de um assembly.  
  
2.  No **Solution Explorer**, selecione o nó do projeto VSIX. Abaixo do Gerenciador de soluções, você deve ver o **propriedades** janela. Se você não fizer isso, selecione **exibição > janela propriedades**, ou pressione **F4**. Na janela Propriedades, selecione os campos a seguir para `true`:  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  Adicione o assembly como um ativo para o projeto do VSIX. Abra o arquivo source.extension.vsixmanifest e selecione o **ativos** guia. No **adicionar novo ativo** janela, para **tipo** selecione **Microsoft.VisualStudio.Assembly**, para **fonte** selecione **um projeto na solução atual**e para **projeto** selecione **MyProjectWizard**.  
  
4.  Adicione as seguintes referências ao projeto VSIX. (No **Solution Explorer**, sob o VSIX selecione do nó do projeto **referências**, com o botão direito e selecione **adicionar referência**.) No **adicionar referência** caixa de diálogo, no **Framework** guia, localize o **System. Windows Forms** assembly e selecioná-lo. Agora selecione o **extensões** localizar na guia o **EnvDTE** assembly e selecioná-lo. Também encontrar o **Microsoft.VisualStudio.TemplateWizardInterface** assembly e selecioná-lo. Clique em **OK**.  
  
5.  Adicione uma classe para a implementação do Assistente para o projeto do VSIX. (No Gerenciador de soluções, clique com botão direito no nó do projeto VSIX e selecione **adicionar**, em seguida, **Novo Item**, em seguida, **classe**.) Nomeie a classe **WizardImplementation**.  
  
6.  Substitua o código no **WizardImplementationClass.cs** arquivo com o código a seguir:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.TemplateWizard;  
    using System.Windows.Forms;  
    using EnvDTE;  
  
    namespace MyProjectWizard  
    {  
        public class WizardImplementation:IWizard  
        {  
            private UserInputForm inputForm;  
            private string customMessage;  
  
            // This method is called before opening any item that   
            // has the OpenInEditor attribute.  
            public void BeforeOpeningFile(ProjectItem projectItem)  
            {  
            }  
  
            public void ProjectFinishedGenerating(Project project)  
            {  
            }  
  
            // This method is only called for item templates,  
            // not for project templates.  
            public void ProjectItemFinishedGenerating(ProjectItem   
                projectItem)  
            {  
            }  
  
            // This method is called after the project is created.  
            public void RunFinished()  
            {  
            }  
  
            public void RunStarted(object automationObject,  
                Dictionary<string, string> replacementsDictionary,  
                WizardRunKind runKind, object[] customParams)  
            {  
                try  
                {  
                    // Display a form to the user. The form collects   
                    // input for the custom message.  
                    inputForm = new UserInputForm();  
                    inputForm.ShowDialog();  
  
                    customMessage = UserInputForm.CustomMessage;  
  
                    // Add custom parameters.  
                    replacementsDictionary.Add("$custommessage$",   
                        customMessage);  
                }  
                catch (Exception ex)  
                {  
                    MessageBox.Show(ex.ToString());  
                }  
            }  
  
            // This method is only called for item templates,  
            // not for project templates.  
            public bool ShouldAddProjectItem(string filePath)  
            {  
                return true;  
            }          
        }  
    }  
    ```  
  
     O **UserInputForm** referenciado neste código será implementado mais tarde.  
  
     O `WizardImplementation` classe contém implementações de método para cada membro do <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. Neste exemplo, apenas o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> método executa uma tarefa. Todos os outros métodos não fazer nada ou retornar `true`.  
  
     O <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> método aceita quatro parâmetros:  
  
    -   Um <xref:System.Object> parâmetro que pode ser convertido para a raiz <xref:EnvDTE._DTE> objeto, para que você possa personalizar o projeto.  
  
    -   Um <xref:System.Collections.Generic.Dictionary%602> parâmetro que contém uma coleção de todos os parâmetros pré-definidos no modelo. Para obter mais informações sobre parâmetros de modelo, consulte [parâmetros de modelo](../ide/template-parameters.md).  
  
    -   Um <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> parâmetro que contém informações sobre o tipo de modelo está sendo usado.  
  
    -   Um <xref:System.Object> matriz que contém um conjunto de parâmetros passados para o assistente pelo Visual Studio.  
  
     Este exemplo adiciona um valor de parâmetro de formulário de entrada do usuário para o <xref:System.Collections.Generic.Dictionary%602> parâmetro. Cada ocorrência da `$custommessage$` parâmetro no projeto será substituído pelo texto inserido pelo usuário. Você deve adicionar os seguintes assemblies ao seu projeto: **sistema** e **System. Drawing**.
  
7.  Agora, crie o **UserInputForm**. No **WizardImplementation.cs** arquivo, adicione o seguinte código após o final do **WizardImplementation** classe.  
  
    ```csharp  
    public partial class UserInputForm : Form  
        {  
            private static string customMessage;  
            private TextBox textBox1;  
            private Button button1;  
  
            public UserInputForm()  
            {  
                this.Size = new System.Drawing.Size(155, 265);   
  
                button1 = new Button();  
                button1.Location = new System.Drawing.Point(90, 25);  
                button1.Size = new System.Drawing.Size(50, 25);  
                button1.Click += button1_Click;  
                this.Controls.Add(button1);  
  
                textBox1 = new TextBox();  
                textBox1.Location = new System.Drawing.Point(10, 25);  
                textBox1.Size = new System.Drawing.Size(70, 20);  
                this.Controls.Add(textBox1);  
            }  
            public static string CustomMessage  
            {  
                get  
                {  
                    return customMessage;  
                }  
                set  
                {  
                    customMessage = value;  
                }     
            }  
            private void button1_Click(object sender, EventArgs e)  
            {  
                customMessage = textBox1.Text;  
                this.Close();
            }  
        }  
    ```  
  
     Formulário de entrada do usuário fornece um formulário simples para inserir um parâmetro personalizado. O formulário contém uma caixa de texto denominada `textBox1` e um botão chamado `button1`. Quando o botão é clicado, o texto da caixa de texto é armazenado no `customMessage` parâmetro.  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>O Assistente de conexão para o modelo personalizado  
 Para o modelo de projeto personalizado usar o assistente personalizado, é necessário assinar o assembly do assistente e adicione algumas linhas no seu modelo de projeto personalizados para que ele saiba onde encontrar a implementação do assistente quando um novo projeto é criado.  
  
1.  Assine o assembly. No **Solution Explorer**, selecione o projeto VSIX, com o botão direito e selecione **propriedades do projeto**.  
  
2.  No **propriedades do projeto** janela, selecione o **assinatura** guia no **assinatura** guia seleção **assinar o assembly**. No **escolher um arquivo de chave de nome forte** campo, selecione  **\<Novo >**. No **criar chave de nome forte** janela, no **nome do arquivo de chave** , digite **key.snk**. Desmarque o **proteger o arquivo com uma senha de chaves** campo.  
  
3.  No **Solution Explorer**, selecione o projeto do VSIX e encontrar o **propriedades** janela.  
  
4.  Definir o **diretório de saída para a saída de compilação de cópia** campo **true**. Isso permite que o assembly a ser copiado para o diretório de saída quando a solução é reconstruída. Ainda está contido no arquivo .vsix. Você precisa ver o assembly para descobrir a chave de assinatura.  
  
5.  Recompile a solução.  
  
6.  Agora você pode encontrar o arquivo key.snk no diretório do projeto MyProjectWizard (**\<seu local de disco > \MyProjectTemplate\MyProjectWizard\key.snk**). Copie o arquivo key.snk.  
  
7.  Vá para o diretório de saída e localize o assembly (**\<seu local de disco > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**). Cole o arquivo key.snk aqui. (Isso não é absolutamente necessário, mas ele facilitará as etapas a seguir).  
  
8.  Abra uma janela de comando e altere o diretório no qual o assembly foi criado.  
  
9. Localizar o **sn.exe** ferramenta de assinatura. Por exemplo, em um sistema de operacional de 64 bits do Windows 10, um caminho típico seria o seguinte:  
  
     **C:\Program arquivos (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 ferramentas**  
  
     Se você não encontrar a ferramenta, tente executar **onde /R.  Sn.exe** na janela de comando. Anote o caminho.  
  
10. Extrai a chave pública do arquivo key.snk. Na janela de comando, digite:  
  
     **\<local do sn.exe > \sn.exe -p key.snk outfile.key.**  
  
     Não se esqueça de colocar o caminho de sn.exe entre aspas se houver espaços em nomes de diretório!  
  
11. Obter token de chave pública do outfile:  
  
     **\<local do sn.exe > \sn.exe -t outfile.key.**  
  
     Novamente, não se esqueça de aspas. Você deve ver uma linha na saída desta  
  
     **Token de chave pública é <token>**  
  
     Anote esse valor.  
  
12. Adicione a referência para o assistente personalizado para o arquivo. vstemplate do modelo de projeto. No Solution Explorer, localize o arquivo chamado MyProjectTemplate.vstemplate e abri-lo. Após o final do \<TemplateContent > seção, adicione a seção a seguir:  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     Onde **MyProjectWizard** é o nome do assembly, e **token** é o token que você copiou na etapa anterior.  
  
13. Salvar todos os arquivos no projeto e recompile.  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>Adicionando o parâmetro personalizado para o modelo  
 Neste exemplo, o projeto usado como modelo exibe a mensagem especificada no formulário de entrada do usuário do assistente personalizado.  
  
1.  No Solution Explorer, vá até o **MyProjectTemplate** do projeto e abra **Class1.cs**.  
  
2.  No `Main` método do aplicativo, adicione a seguinte linha de código.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     O parâmetro `$custommessage$` é substituído pelo texto inserido no formulário de entrada do usuário quando um projeto é criado a partir do modelo.  
  
 Aqui está o arquivo de código completo antes de ser exportado para um modelo.  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="using-the-custom-wizard"></a>Usando o assistente personalizado  
 Agora você pode criar um projeto de modelo e usar o assistente personalizado.  
  
1.  Recompile a solução e iniciar a depuração. Uma segunda instância do Visual Studio deve ser exibida.  
  
2.  Crie um novo projeto de MyProjectTemplate. (**Arquivo > Novo > projeto > Visual C# > MyProjectTemplate**)  
  
3.  No **novo projeto** caixa de diálogo, localize seu modelo, digite um nome e clique em **Okey**.  
  
     Abre o formulário de entrada de usuário do assistente.  
  
4.  Digite um valor para o parâmetro personalizado e clique no botão.  
  
     Fecha o formulário de entrada de usuário do assistente e um projeto é criado a partir do modelo.  
  
5.  Em **Solution Explorer**, clique no arquivo de código fonte e clique em **Exibir código**.  
  
     Observe que `$custommessage$` foi substituído pelo texto inserido no formulário de entrada do usuário do assistente.  
  
## <a name="see-also"></a>Consulte também  

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
[Personalizando modelos](../ide/customizing-project-and-item-templates.md)  
[Elemento WizardExtension (Modelos do Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)  
[Pacotes do NuGet em modelos do Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
