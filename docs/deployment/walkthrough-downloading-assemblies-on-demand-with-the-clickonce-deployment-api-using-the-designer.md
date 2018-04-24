---
title: 'Passo a passo: Baixando Assemblies por demanda com a implantação do ClickOnce usando o Designer de API | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fef9486f6bbcbea0d330aaf16fe625642f1e662f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Instruções passo a passo: baixando assemblies por demanda com a API de implantação do ClickOnce usando o designer
Por padrão, todos os assemblies são incluídos em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo são baixados quando o aplicativo for executado pela primeira vez. No entanto, pode haver partes do seu aplicativo que são usados por um pequeno conjunto de usuários. Nesse caso, você deseja fazer o download de um assembly somente quando você cria um de seus tipos. A instrução a seguir demonstra como marcar determinados assemblies em seu aplicativo como "opcional", e classes como baixá-los usando o <xref:System.Deployment.Application> namespace quando os requer o common language runtime.  
  
> [!NOTE]
>  Seu aplicativo terá que ser executado em confiança total para usar este procedimento.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, clique em **Importar e exportar configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Para criar um projeto que usa um assembly sob demanda com o Visual Studio  
  
1.  Criar um novo projeto do Windows Forms no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto**. Escolha um **biblioteca de classes** projeto na caixa de diálogo e nomeie-o `ClickOnceLibrary`.  
  
    > [!NOTE]
    >  No Visual Basic, é recomendável que você modifique as propriedades do projeto para alterar o namespace raiz para este projeto para `Microsoft.Samples.ClickOnceOnDemand` ou a um namespace de sua escolha. Para simplificar, os dois projetos neste passo a passo estão no mesmo namespace.  
  
2.  Definir uma classe denominada `DynamicClass` com uma única propriedade denominada `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
3.  Selecione o projeto do Windows Forms em **Gerenciador de soluções**. Adicione uma referência para o <xref:System.Deployment.Application> referência de assembly e um projeto para o `ClickOnceLibrary` projeto.  
  
    > [!NOTE]
    >  No Visual Basic, é recomendável que você modifique as propriedades do projeto para alterar o namespace raiz para este projeto para `Microsoft.Samples.ClickOnceOnDemand` ou a um namespace de sua escolha. Para simplificar, os dois projetos neste passo a passo estão localizados no mesmo namespace.  
  
4.  O formulário, clique **Exibir código** no menu e adicione as seguintes referências para o formulário.  
  
     [!code-csharp[ClickOnceOnDemand#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.cs)]
     [!code-vb[ClickOnceOnDemand#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
5.  Adicione o código a seguir para baixar este assembly sob demanda. Este código mostra como mapear um conjunto de módulos (assemblies) para um nome de grupo usando um genérico <xref:System.Collections.DictionaryBase.Dictionary%2A> classe. Porque estamos apenas baixar um único assembly neste passo a passo, há apenas um assembly no nosso grupo. Um aplicativo real, você provavelmente desejará fazer o download de todos os assemblies relacionados a um único recurso em seu aplicativo ao mesmo tempo. A tabela de mapeamento permite que você faça isso facilmente por meio da associação todas as DLLs que pertencem a um recurso com um nome de grupo de download.  
  
     [!code-csharp[ClickOnceOnDemand#2](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.cs)]
     [!code-vb[ClickOnceOnDemand#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
6.  Sobre o **exibição** menu, clique em **caixa de ferramentas**. Arraste um <xref:System.Windows.Forms.Button> do **caixa de ferramentas** para o formulário. Clique duas vezes no botão e adicione o seguinte código para o <xref:System.Windows.Forms.Control.Click> manipulador de eventos.  
  
     [!code-csharp[ClickOnceOnDemand#3](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.cs)]
     [!code-vb[ClickOnceOnDemand#3](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.vb)]  
  
## <a name="marking-assemblies-as-optional"></a>Marcar Assemblies como opcional  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Marcar assemblies como opcionais no seu aplicativo ClickOnce usando o Visual Studio  
  
1.  Clique com botão direito no projeto do Windows Forms no **Solution Explorer** e clique em **propriedades**. Selecione o **publicar** guia.  
  
2.  Clique o **arquivos de aplicativo** botão.  
  
3.  Localize a listagem para ClickOnceLibrary.dll. Definir o **Status da publicação** caixa suspensa para **incluir**.  
  
4.  Expanda o **grupo** caixa suspensa e selecione **novo**. Digite o nome `ClickOnceLibrary` como o nome do novo grupo.  
  
5.  Continuar a publicar seu aplicativo conforme descrito em [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Marcar assemblies como opcionais no seu aplicativo ClickOnce usando a ferramenta de edição e geração de manifesto, cliente gráfico (MageUI.exe)  
  
1.  Criar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos conforme descrito em [passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Antes de fechar MageUI.exe, selecione a guia que contém o manifesto do aplicativo de implantação e nessa guia, selecione o **arquivos** guia.  
  
3.  Localizar ClickOnceLibrary.dll na lista de arquivos de aplicativo e defina seu **tipo de arquivo** coluna **nenhum**. Para o **grupo** coluna, digite `ClickOnceLibrary.dll`.  
  
## <a name="testing-the-new-assembly"></a>Testar o novo Assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Para testar seu assembly sob demanda  
  
1.  Iniciar o aplicativo implantado com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Quando o formulário principal for exibida, pressione a <xref:System.Windows.Forms.Button>. Você deve ver uma cadeia de caracteres em uma janela de caixa de mensagem que lê, "Olá, mundo!"  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Deployment.Application.ApplicationDeployment>