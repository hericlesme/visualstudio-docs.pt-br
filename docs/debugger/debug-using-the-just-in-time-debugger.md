---
title: Depurar usando o depurador Just-in | Microsoft Docs
ms.custom: ''
ms.date: 09/24/18
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a2e6cfbd6d26d575bab5d7592f320779ffd8888
ms.sourcegitcommit: 000cdd1e95dd02e99a7c7c1a34c2f8fba6a632af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168390"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Depurar usando o depurador Just-in-no Visual Studio
Depuração Just-In-Time inicia o Visual Studio automaticamente quando uma exceção ou uma falha ocorre em um aplicativo que está em execução fora do Visual Studio. Isso permite que você teste seu aplicativo quando o Visual Studio não está em execução e iniciar a depuração com o Visual Studio quando ocorre um problema.

Depuração Just-In-Time funciona para aplicativos de desktop do Windows. Ele não funciona para aplicativos universais do Windows e não funciona para código gerenciado que é hospedado em um aplicativo nativo, como visualizadores.

> [!TIP]
> Se você quiser apenas saber como responder a Just-in-Time caixa de diálogo do depurador, consulte [neste tópico](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a> Habilitar ou desabilitar Just-In-Time a depuração
Você pode habilitar ou desabilitar a depuração do Visual Studio Just-In-Time **Ferramentas > Opções** caixa de diálogo.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Para habilitar ou desabilitar a depuração Just-In-Time

1.  Abra o Visual Studio com privilégios de administrador (com o botão direito e escolha **executar como administrador**).

    Ativando ou desativando o Just-In-Time depuração define uma chave do registro e podem ser necessários privilégios de administrador para alterar essa chave.

2. No menu **Ferramentas**, clique em **Opções**.

2.  No **opções** diálogo caixa, expanda o **depuração** nó.

3.  No **Debugging** nó, selecione **Just-In-Time**.

    ![Habilitar ou desabilitar a depuração JIT](../debugger/media/dbg-jit-enable-or-disable.png "habilitar ou desabilitar a depuração JIT")

4.  No **just-in-habilitar a depuração desses tipos de código** caixa, marque ou desmarque os tipos de programa relevantes: **gerenciado**, **nativo**, ou **Script**.

5.  Clique em **OK**.

    Se você habilitar o Just-in-Time depurador, mas você não vê-lo em uma falha de aplicativo ou uma exceção, consulte [erros de depuração Just-In-Time](#jit_errors).

A depuração Just-In-Time ainda poderá ser habilitada, mesmo que o Visual Studio não esteja mais instalado no seu computador. Quando o Visual Studio não estiver instalado, você não é possível desabilitar a depuração do Visual Studio Just-In-Time **opções** caixa de diálogo. Nesse caso, você poderá desabilitar a depuração Just-In-Time editando o Registro do Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Para desabilitar a depuração Just-In-Time editando o Registro

1.  Sobre o **iniciar** menu, procure e execute `regedit.exe`

2.  No **Editor do registro** janela, localize e exclua as seguintes entradas do registro:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\DbgManagedDebugger

    ![Chave do registro JIT](../debugger/media/dbg-jit-registry.png "chave do registro JIT")

3.  Se o computador estiver executando um sistema operacional de 64 bits, exclua as seguintes entradas de registro também:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger

4.  Tenha cuidado para não excluir ou não alterar acidentalmente quaisquer outras chaves do Registro.

5.  Fechar o **Editor do registro** janela.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Para habilitar a depuração Just-In-Time de um formulário do Windows

1.  Por padrão, os aplicativos do Windows Forms têm um manipulador de exceção de nível superior que permite que o programa continue a executar se puder recuperar. Por exemplo, se seu aplicativo de formulários do Windows gera uma exceção sem tratamento, você verá uma caixa de diálogo semelhante à seguinte:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Para habilitar Just-In-Time a depuração de um aplicativo do Windows Forms, você deve executar as seguintes etapas adicionais:

2.  Defina a `jitDebugging` de valor para `true` na `system.windows.form` seção Machine. config ou  *\<nome do aplicativo >*. arquivo exe. config:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  No aplicativo C++ do Windows Form, você também deve definir `DebuggableAttribute` em um arquivo .config ou no seu código. Se você compilar com [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) e sem [/Og](/cpp/build/reference/og-global-optimizations), o compilador definirá esse atributo para você. Se você desejar depurar uma compilação de liberação não otimizada, no entanto, deverá definir isso por conta própria. Você pode fazer isso adicionando a seguinte linha ao arquivo de AssemblyInfo.cpp do seu aplicativo:

    ```cpp
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Para obter mais informações, consulte <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Use a depuração Just-In-Time
 Esta seção mostra o que acontece quando um executável gera uma exceção.

 Você deve ter o Visual Studio instalado para executar estas etapas. Se você não tiver o Visual Studio, você pode baixar gratuitamente [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

 Certifique-se de que Just-In-Time está depurando [habilitado](#BKMK_Enabling).

 Para os fins desta seção, criaremos um aplicativo de console c# no Visual Studio gera uma [NullReferenceException](/dotnet/api/system.nullreferenceexception).

 No Visual Studio, crie um aplicativo de console c# (**arquivo > Novo > projeto > Visual c# > aplicativo de Console**) denominada **ThrowsNullException**. Para obter mais informações sobre como criar projetos no Visual Studio, consulte [instruções passo a passo: criar um aplicativo simples](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Quando o projeto é aberto no Visual Studio, abra o arquivo Program.cs. Substitua o método Main () com o código a seguir, que imprime uma linha para o console e, em seguida, lança uma NullReferenceException:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  Para que este procedimento trabalhar um [configuração de versão](../debugger/how-to-set-debug-and-release-configurations.md), você precisará desativar [Just My Code](../debugger/just-my-code.md). No Visual Studio, clique em **Ferramentas > Opções**. No **opções** caixa de diálogo, selecione **depuração**. Remover a seleção de **habilitar apenas meu código**.

 Compile a solução (no Visual Studio, escolha **compilar > recompilar solução**). Você pode escolher a depuração ou a configuração de versão (escolha **depurar** para a experiência de depuração completa). Para obter mais informações sobre configurações de build, consulte [Noções básicas sobre configurações de build](../ide/understanding-build-configurations.md).

 O processo de compilação cria um executável ThrowsNullException.exe. Você pode encontrá-lo na pasta em que você criou o projeto do c#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** ou **...\ThrowsNullException\ThrowsNullException\bin\Release**.

 Clique duas vezes o ThrowsNullException.exe. Você deverá ver uma janela de comando como este:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Depois de alguns segundos, será exibida uma janela de erro:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Não clique **Cancelar**! Depois de alguns segundos, você deverá ver dois botões, **Debug** e **fechar programa**. Clique em **depurar**.

> [!CAUTION]
>  Se seu aplicativo contém código não confiável, aparecerá uma caixa de diálogo com um aviso de segurança. Essa caixa de diálogo permite que você decida se deseja continuar com a depuração. Antes de prosseguir com a depuração, decida se você confia no código. Você mesmo escreveu o código? Você confia no programador? Se o aplicativo está sendo executado em um computador remoto, você reconhece o nome do processo? Mesmo que o aplicativo seja executado localmente, isso não significa necessariamente que ele é confiável. Considere a possibilidade de código mal-intencionado em execução no seu computador. Se você decidir que o código você está prestes a depurar é confiável, clique em **depurar**. Caso contrário, clique em **Don't Debug**.

 O **depurador do Visual Studio Just-in-** janela é exibida:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 Sob **possíveis depuradores**, você deverá ver que o **nova instância do Microsoft Visual Studio <available version>**  linha está selecionada. Se ainda não estiver selecionado, selecione-o agora.

 Na parte inferior da janela, sob **você deseja depurar usando o depurador selecionado?**, clique em **Sim**.

 O projeto de ThrowsNullException é aberto em uma nova instância do Visual Studio, com execução interrompida na linha que gerou a exceção:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Você pode iniciar a depuração no momento. Se esse fosse um aplicativo real, você precisa descobrir por que o código está lançando a exceção.

## <a name="jit_errors"></a> Erros de depuração Just-In-Time
 Se você não vir a caixa de diálogo quando o programa falhar e precisa habilitar o recurso, isso pode ser devido a configurações de relatório de erros do Windows em seu computador. Certifique-se de adicionar um **desabilitado** valor para as seguintes chaves do registro e definir o valor como 1:

* Relatório de erros do HKLM\Software\Microsoft\Windows\Windows
* Relatório de erros do HKLM\Software\WOW6432Node\Microsoft\Windows\Windows
 
Para obter mais informações sobre essas configurações, consulte [. Configurações WER](https://docs.microsoft.com/windows/desktop/wer/wer-settings).

Além disso, você pode ver as seguintes mensagens de erro que estão associadas com Just-In-Time de depuração.

- **Não é possível anexar ao processo de travamento. O programa especificado não é um programa do Windows ou MS-DOS.**

    Esse erro ocorre quando você tenta anexar a um processo em execução como outro usuário.

    Para contornar esse problema, inicie o Visual Studio, abra o **anexar ao processo** caixa de diálogo a **Debug** menu e localize o processo que você deseja depurar no **processos disponíveis**lista. Se você não souber o nome do processo, examine os **depurador do Visual Studio Just-in-** caixa de diálogo e anote a ID de processo. Selecione o processo na **processos disponíveis** lista e clique em **Attach**. No **depurador do Visual Studio Just-in-** caixa de diálogo, clique em **não** para descartar a caixa de diálogo.

- **Não foi possível iniciar o depurador porque nenhum usuário está conectado.**

    Este erro ocorre quando a depuração Just-In-Time tenta iniciar o Visual Studio em um computador no qual não há nenhum usuário conectado ao console. Como nenhum usuário está conectado, não há sessão de usuário para exibir a caixa de diálogo Depuração Just-In-Time.

    Para corrigir esse problema, conecte-se ao computador.

- **Classe não registrada.**

    Este erro indica que o depurador tentou criar uma classe COM não registrada, provavelmente devido a um problema de instalação.

    Para corrigir o problema, use o disco de instalação para reinstalar ou reparar sua instalação do Visual Studio.

## <a name="see-also"></a>Consulte também
 [Segurança do depurador](../debugger/debugger-security.md) [Noções básicas do depurador](../debugger/getting-started-with-the-debugger.md) [Just-In-Time, depuração, caixa de diálogo Opções](../debugger/just-in-time-debugging-options-dialog-box.md) [aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou você não tiver certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
