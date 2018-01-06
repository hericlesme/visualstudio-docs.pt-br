---
title: Implantando componentes do COM o ClickOnce | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a63073e86c3584253e67bf4d77f43006104de075
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-com-components-with-clickonce"></a>Implantando componentes do COM com o ClickOnce
Implantação de componentes legados COM tradicionalmente foi uma tarefa difícil. Componentes precisam ser registrado globalmente e, portanto, podem causar efeitos colaterais indesejáveis entre aplicativos sobrepostos. Essa situação geralmente não é um problema em aplicativos do .NET Framework porque componentes são completamente isolados a um aplicativo ou são compatíveis com o lado a lado. O Visual Studio permite que você implante componentes isolados no sistema de operacional superior ou o Windows XP.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Fornece um mecanismo fácil e seguro para implantar seus aplicativos .NET. No entanto, se seus aplicativos usam componentes COM herdados, você precisará executar etapas adicionais para implantá-los. Este tópico descreve como implantar componentes COM isolados e fazem referência a componentes nativo (por exemplo, do Visual C++ ou Visual Basic 6.0).  
  
 Para obter mais informações sobre a implantação de componentes COM isolados, consulte "Simplifique a implantação de aplicativos com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM sem registro" em [http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## <a name="registration-free-com"></a>COM sem registro  
 COM sem registro é uma nova tecnologia de implantação e ativando a isoladas componentes do COM. Ele funciona, colocando a biblioteca de tipos de todas as do componente e informações de registro que é normalmente instaladas no registro do sistema em um arquivo XML chamado um manifesto, armazenados na mesma pasta que o aplicativo.  
  
 Isolar um componente COM requer que ele ser registrado na máquina do desenvolvedor, mas ele não precisa ser registrado no computador do usuário final. Para isolar um componente COM, tudo o que você precisa fazer é definir sua referência **isolado** propriedade **True**. Por padrão, essa propriedade é definida como **False**, indicando que ele deve ser tratado como uma referência COM registrado. Se essa propriedade for **True**, ele faz com que um manifesto a ser gerado para este componente em tempo de compilação. Ele também faz com que os arquivos correspondentes a serem copiados para a pasta do aplicativo durante a instalação.  
  
 Quando o gerador de manifesto encontra uma referência COM isolado, enumera todos os `CoClass` entradas na biblioteca de tipos do componente, correspondência de cada entrada com seus dados de registro correspondente e geração de manifesto definições para o COM todos os classes no arquivo de biblioteca de tipo.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Implantação de componentes COM sem registro usando o ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]tecnologia de implantação é adequada para a implantação de componentes COM isolado, porque ambos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM sem registro exige que um componente tem um manifesto para ser implantado.  
  
 Normalmente, o autor do componente deve fornecer um manifesto. Caso contrário, no entanto, o Visual Studio é capaz de gerar um manifesto automaticamente para um componente COM. A geração de manifesto é executada durante o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] processo de publicação; para obter mais informações, consulte [publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md). Esse recurso também permite que você aproveite os componentes herdados que você criou em ambientes de desenvolvimento anteriores, como Visual Basic 6.0.  
  
 Há duas maneiras que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implanta componentes COM:  
  
-   Use o inicializador para implantar seus componentes COM. Isso funciona em todas as plataformas com suporte.  
  
-   Use a implantação do componente nativo isolamento (também conhecido como COM sem registro). No entanto, isso só funcionará em um sistema de operacional superior ou o Windows XP.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Exemplo de isolar e implantar um componente simples  
 Para demonstrar a implantação de componentes COM sem registro, este exemplo cria um aplicativo baseado em Windows no Visual Basic que faz referência a um componente COM nativo isolado criado usando o Visual Basic 6.0 e implantá-lo usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Primeiro, você precisará criar o componente nativo:  
  
##### <a name="to-create-a-native-com-component"></a>Para criar um componente nativo  
  
1.  Usando o Visual Basic 6.0, do **arquivo** menu, clique em **novo**, em seguida, **projeto**.  
  
2.  No **novo projeto** caixa de diálogo, selecione o **Visual Basic** nó e selecione um **ActiveX DLL** projeto. Na caixa **Nome**, digite `VB6Hello`.  
  
    > [!NOTE]
    >  Somente tipos de projeto ActiveX DLL e o controle ActiveX são compatíveis com sem registro COM; Não há suporte para tipos de projeto EXE ActiveX e documento ActiveX.  
  
3.  Em **Solution Explorer**, clique duas vezes em **Class1** para abrir o editor de texto.  
  
4.  Em Class1. vb, adicione o seguinte código após o código gerado para o `New` método:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Crie o componente. Do **criar** menu, clique em **compilar solução**.  
  
> [!NOTE]
>  COM sem registro suporta apenas DLLs e COM controles de tipos de projeto. Não é possível usar EXEs com sem registro COM.  
  
 Agora você pode criar um aplicativo baseado em Windows e adicionar uma referência ao componente COM a ele.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Para criar um aplicativo baseado no Windows usando um componente COM  
  
1.  Usando o Visual Basic, do **arquivo** menu, clique em **novo**, em seguida, **projeto**.  
  
2.  No **novo projeto** caixa de diálogo, selecione o **Visual Basic** nó e selecione **aplicativo do Windows**. Na caixa **Nome**, digite `RegFreeComDemo`.  
  
3.  Em **Solution Explorer**, clique no **Mostrar todos os arquivos** botão para exibir as referências do projeto.  
  
4.  Clique com botão direito do **referências** nó e selecione **adicionar referência** no menu de contexto.  
  
5.  No **adicionar referência** caixa de diálogo, clique o **procurar** guia, navegue até VB6Hello.dll e selecioná-lo.  
  
     Um **VB6Hello** referência aparece na lista de referências.  
  
6.  Aponte para o **caixa de ferramentas**, selecione um **botão** controlar e arraste-o para o **Form1** formulário.  
  
7.  No **propriedades** janela, defina o botão **texto** propriedade **Hello**.  
  
8.  Clique duas vezes no botão para adicionar o código do manipulador e no arquivo de código, adicione código para que o manipulador lê da seguinte maneira:  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Execute o aplicativo. Do **depurar** menu, clique em **iniciar depuração**.  
  
 Em seguida, você precisa isolar o controle. Cada componente COM que o aplicativo usa é representado no seu projeto como uma referência de COM. Essas referências são visíveis no **referências** nó o **Solution Explorer** janela. (Observe que você pode adicionar referências diretamente usando o **adicionar referência** comando o **projeto** menu, ou indiretamente, arrastando um controle ActiveX para seu formulário.)  
  
 As etapas a seguir mostram como isolar o componente COM e publicar o aplicativo atualizado que contém o controle isolado:  
  
##### <a name="to-isolate-a-com-component"></a>Para isolar um componente COM  
  
1.  Em **Solution Explorer**, no **referências** nó, selecione o **VB6Hello** referência.  
  
2.  No **propriedades** janela, alterar o valor da **isolado** propriedade **False** para **True**.  
  
3.  Do **criar** menu, clique em **compilar solução**.  
  
 Agora, quando você pressionar F5, a aplicativo funciona conforme o esperado, mas ele está em execução em COM. sem registro Para provar isso, tente cancelar o registro do componente VB6Hello.dll e executar RegFreeComDemo1.exe fora do IDE do Visual Studio. Desta vez, quando o botão é clicado, ele ainda funciona. Se você renomear temporariamente o manifesto do aplicativo, ele novamente falhará.  
  
> [!NOTE]
>  Você pode simular a ausência de um componente COM por temporariamente ao cancelar o registro. Abra um prompt de comando, vá para a pasta sistema digitando `cd /d %windir%\system32`, em seguida, cancelar o registro do componente digitando `regsvr32 /u VB6Hello.dll`. Você pode registrá-lo novamente, digitando `regsvr32 VB6Hello.dll`.  
  
 A etapa final é publicar o aplicativo usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Para publicar uma atualização do aplicativo com um componente COM isolado  
  
1.  Do **criar** menu, clique em **RegFreeComDemo publicar**.  
  
     O Assistente de Publicação será exibido.  
  
2.  No Assistente de publicação, especifique um local no disco do computador local em que você pode acessar e examine os arquivos publicados.  
  
3.  Clique em **concluir** para publicar o aplicativo.  
  
 Se você examinar os arquivos publicados, você notará que o arquivo Sysmon está incluído. O controle é totalmente isolado nesse aplicativo, o que significa que, se o computador do usuário final tiver outro aplicativo usando uma versão diferente do controle, ele não pode interferir com este aplicativo.  
  
## <a name="referencing-native-assemblies"></a>Referenciando Assemblies nativo  
 Visual Studio oferece suporte a referências a nativos do Visual Basic 6.0 ou assemblies C++; Essas referências são chamadas de referências nativo. Você pode determinar se uma referência é nativo, verificando se seu **tipo de arquivo** está definida como **nativo** ou **ActiveX**.  
  
 Para adicionar uma referência nativa, use o **adicionar referência** de comando e navegue para o manifesto. Alguns componentes colocar o manifesto dentro da DLL. Nesse caso, você poderá simplesmente própria DLL e Visual Studio irá adicioná-lo como uma referência nativa se detectar que o componente contém um manifesto inserido. O Visual Studio automaticamente também incluirá todos os arquivos dependentes ou assemblies listados no manifesto, se estiverem na mesma pasta que o componente referenciado.  
  
 Isolamento de controle COM torna fácil de implantar os componentes COM que ainda não tenham manifestos. No entanto, se um componente é fornecido com um manifesto, você pode referenciar diretamente o manifesto. Na verdade, você sempre deve usar o manifesto fornecido pelo autor do componente sempre que possível, em vez de usar o **isolado** propriedade.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitações de implantação de componente de COM sem registro  
 COM sem registro fornece vantagens limpar técnicas tradicionais de implantação. No entanto, há algumas limitações e restrições que também devem ser indicadas. A maior limitação é que ele funciona apenas no Windows XP ou superior. A implementação de COM sem registro exigiu alterações para a maneira na qual os componentes são carregados no sistema operacional principal. Infelizmente, não há nenhuma camada de suporte de nível inferior para COM. sem registro  
  
 Nem todos os componentes é um candidato adequado para COM. sem registro Um componente não é um adequado se qualquer uma das seguintes opções for verdadeira:  
  
-   O componente é um servidor fora do processo. Não há suporte para servidores EXE; somente as DLLs são suportadas.  
  
-   O componente é parte do sistema operacional, ou é um componente do sistema, como XML, o Internet Explorer ou o Microsoft Data Access Components (MDAC). Você deve seguir a diretiva de redistribuição do autor do componente; Verifique com seu fornecedor.  
  
-   O componente é parte de um aplicativo, como o Microsoft Office. Por exemplo, você não deve tentar isolar o modelo de objeto do Microsoft Excel. Isso faz parte do Office e só pode ser usado em um computador com o produto completo do Office instalado.  
  
-   O componente é destinado ao uso como um suplemento ou um snap-in, por exemplo um suplemento do Office ou um controle em um navegador da Web. Esses componentes geralmente exigem algum tipo de esquema de registro definido pelo ambiente de hospedagem está além do escopo do manifesto em si.  
  
-   O componente gerencia um dispositivo físico ou virtual do sistema, por exemplo, um driver de dispositivo para o spooler de impressão.  
  
-   O componente é redistribuível de acesso a dados. Aplicativos de dados geralmente requerem separado de acesso a dados redistribuível ser instalado antes de serem executados. Você não deve tentar isolar componentes, como o controle de dados do Microsoft ADO, OLE DB Microsoft ou Microsoft Data Access Components (MDAC). Em vez disso, se seu aplicativo usa MDAC ou SQL Server Express, você deve defini-las como pré-requisitos; consulte [como: instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
 Em alguns casos, pode ser possível para o desenvolvedor do componente reprojetá-lo para COM. sem registro Se isso não for possível, você pode criar e publicar aplicativos que dependem deles por meio do esquema padrão do registro usando o Bootstrapper. Para obter mais informações, consulte [criação de pacotes de Bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
 Um componente COM só pode ser isolado uma vez por aplicativo. Por exemplo, não é possível isolar o componente COM mesmo de duas diferentes **biblioteca de classes** projetos que fazem parte do mesmo aplicativo. Isso resultará em um aviso de compilação e o aplicativo não poderá ser carregado no tempo de execução. Para evitar esse problema, a Microsoft recomenda que encapsulam componentes COM em uma biblioteca de classe individual.  
  
 Há vários cenários que COM registro é necessário no computador de um desenvolvedor, mesmo que a implantação do aplicativo não requer registro. O `Isolated` propriedade requer que o componente COM ser registrado na máquina do desenvolvedor para gerar automaticamente o manifesto durante a compilação. Não há não há recursos de captura de registro que invocar o auto-registro durante a compilação. Além disso, todas as classes não são explicitamente definidas na biblioteca de tipo não serão refletidas no manifesto. Ao usar um componente COM um manifesto já existente, como uma referência nativa, o componente não precisará ser registrado no tempo de desenvolvimento. No entanto, o registro é necessário se o componente é um controle ActiveX e você deseja incluir no **caixa de ferramentas** e o designer de formulários do Windows.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)