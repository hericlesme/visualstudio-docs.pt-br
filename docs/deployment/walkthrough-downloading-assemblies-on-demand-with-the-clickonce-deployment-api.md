---
title: 'Passo a passo: Baixando Assemblies por demanda com a API de implantação do ClickOnce | Microsoft Docs'
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
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48ed3828f70424ee328c1fc52873e1a0f7e620aa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31565764"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Instruções passo a passo: baixando assemblies por demanda com a API de implantação do ClickOnce
Por padrão, todos os assemblies incluídos em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo são baixados quando o aplicativo for executado pela primeira vez. No entanto, você pode ter partes de seu aplicativo que são usados por um conjunto pequeno de usuários. Nesse caso, você deseja fazer o download de um assembly somente quando você cria um de seus tipos. A instrução a seguir demonstra como marcar determinados assemblies em seu aplicativo como "opcional", e classes como baixá-los usando o <xref:System.Deployment.Application> namespace quando o common language runtime (CLR) os requer.  
  
> [!NOTE]
>  Seu aplicativo terá que ser executado em confiança total para usar este procedimento.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisará de um dos componentes a seguir para concluir este passo a passo:  
  
-   O SDK do Windows. O SDK do Windows pode ser baixado do Microsoft Download Center.  
  
-   Visual Studio.  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Para criar um projeto que usa um assembly sob demanda  
  
1.  Crie um diretório chamado ClickOnceOnDemand.  
  
2.  Abra o Prompt de comando do SDK do Windows ou o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Prompt de comando.  
  
3.  Altere o diretório ClickOnceOnDemand.  
  
4.  Gere um par de chaves pública/privada usando o seguinte comando:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Usando o bloco de notas ou outro editor de texto, definir uma classe denominada `DynamicClass` com uma única propriedade denominada `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Salvar o texto como um arquivo chamado `ClickOnceLibrary.cs` ou `ClickOnceLibrary.vb`, dependendo do idioma que você usa, para o diretório ClickOnceOnDemand.  
  
7.  Compile o arquivo em um assembly.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Para obter a chave pública token para o assembly, use o seguinte comando:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Criar um novo arquivo usando o texto do editor e insira o código a seguir. Esse código cria um aplicativo do Windows Forms que baixa o assembly ClickOnceLibrary quando necessário.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. No código, localize a chamada para <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Defina`PublicKeyToken` para o valor que você recuperou anteriormente.  
  
12. Salve o arquivo como `Form1.cs` ou `Form1.vb`.  
  
13. Compilá-lo em um executável usando o comando a seguir.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Marcar Assemblies como opcional  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Marcar assemblies como opcionais no seu aplicativo ClickOnce usando MageUI.exe  
  
1.  Usando MageUI.exe, crie um manifesto de aplicativo, conforme descrito em [passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Use as seguintes configurações para o manifesto do aplicativo:  
  
    -   Nomeie o manifesto do aplicativo `ClickOnceOnDemand`.  
  
    -   No **arquivos** página, na linha ClickOnceLibrary.dll, defina o **tipo de arquivo** coluna **nenhum**.  
  
    -   No **arquivos** página, na linha ClickOnceLibrary.dll, tipo `ClickOnceLibrary.dll` no **grupo** coluna.  
  
2.  Usando MageUI.exe, crie um manifesto de implantação, conforme descrito em [passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Use as seguintes configurações para o manifesto de implantação:  
  
    -   Nome do manifesto de implantação `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Testar o novo Assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Para testar seu assembly sob demanda  
  
1.  Carregue seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação em um servidor Web.  
  
2.  Iniciar o aplicativo implantado com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] em um navegador da Web, especificando a URL para o manifesto de implantação. Se você chamar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo `ClickOnceOnDemand`e carregue-o no diretório raiz da adatum.com, a URL seria assim:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Quando o formulário principal for exibida, pressione a <xref:System.Windows.Forms.Button>. Você deve ver uma cadeia de caracteres em uma janela de caixa de mensagem que diz "Olá, mundo!".  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Deployment.Application.ApplicationDeployment>