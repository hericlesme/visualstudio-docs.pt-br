---
title: Solução de problemas e problemas conhecidos (Ferramentas do Visual Studio para Unity) | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: cb1da2ec2c41fcbec78864868d116bcd1684a5b2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31562007"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Solucionando problemas e problemas conhecidos (Visual Studio Tools for Unity)
Nesta seção, você encontrará soluções para problemas comuns das Ferramentas do Visual Studio para Unity, as descrições de problemas conhecidos e aprenderá como ajudar a melhorar as Ferramentas do Visual Studio para Unity por meio de relatórios de erro.

## <a name="troubleshooting"></a>Solução de problemas
Para resolver alguns problemas comuns das Ferramentas do Visual Studio para Unity, consulte as seções a seguir.

### <a name="visual-studio-crashes"></a>O Visual Studio falha
O motivo pode ser que o cache do MEF do Visual Studio está corrompido.

Você deverá remover a pasta a seguir para redefinir o cache do MEF (feche o Visual Studio antes de fazer isso):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Isso deve corrigir o problema. Caso o problema persista, execute um prompt de comando do desenvolvedor do Visual Studio como administrador e use o seguinte comando:

```batch
 devenv /setup
```

### <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problemas com o Visual Studio 2015 e o IntelliSense ou com a coloração de código.
Você deve tentar atualizar o Visual Studio 2015 para atualização 3.

### <a name="shader-files-without-code-coloration-when-using-visual-studio-2017"></a>Arquivos de sombreador sem coloração de código ao usar o Visual Studio de 2017
Certifique-se de que a carga de trabalho de "Desenvolvimento para desktop com C++" esteja instalada na sua instância do Visual Studio de 2017. O analisador de C/C++ usado para coloração de código é fornecido com essa carga de trabalho.

### <a name="visual-studio-hangs"></a>O Visual Studio trava
Vários plug-ins do Unity como Parse, FMOD, UMP (Universal Media Player), ZFBrowser ou navegador inserido usam threads nativos. Isso é um problema quando um plug-in acaba anexando um thread nativo ao tempo de execução, fazendo chamadas de bloqueio para o sistema operacional. Isso significa que o Unity não consegue interromper esse thread para o depurador (ou o recarregamento de domínio) e trava.

Para o FMOD, há uma solução alternativa, você pode passar o [sinalizador](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) de inicialização FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE para desabilitar o processamento assíncrono e executar todo o processamento no thread principal.

### <a name="incompatible-project-in-visual-studio"></a>Projeto incompatível no Visual Studio
Primeiro, verifique se o Visual Studio está definido como seu editor de script externo no Unity (Editar/Preferências/Ferramentas Externas). Em seguida, verifique se o plug-in do Visual Studio está instalado no Unity (Ajuda/Sobre deve exibir uma mensagem, como as Ferramentas do Microsoft Visual Studio para Unity estão habilitadas na parte inferior). Em seguida, verifique se a extensão está instalada corretamente no Visual Studio (Ajuda/Sobre).

### <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Recargas extras, ou o Visual Studio perde todas as janelas abertas
Certifique-se de nunca tocar nos arquivos de projeto diretamente de um processador de ativos ou de qualquer outra ferramenta. Se você realmente precisar manipular o arquivo de projeto, expomos uma API para isso. Consulte a seção de [Problemas com referências de assembly](#Assembly-reference-issues).

Se você tiver recargas extras ou se o Visual Studio estiver perdendo todas as janelas abertas ao recarregar, verifique se você tem os pacotes corretos de direcionamento do .NET instalados. Verifique a seção a seguir sobre estruturas para obter mais informações.

###  <a name="the-debugger-does-not-break-on-exceptions"></a>O depurador não é interrompido quando há exceções
Ao usar o tempo de execução do Unity herdado (equivalente ao .NET 3.5), o depurador sempre será interrompido quando uma exceção ficar sem tratamento (= fora de um bloco try/catch). Se a exceção for manipulada, o depurador usará a janela Configurações de Exceção para determinar se uma interrupção é necessária ou não.

Com o novo tempo de execução (equivalente ao .NET 4.6), o Unity introduziu uma nova forma de gerenciar exceções de usuário e, como resultado, todas as exceções são vistas como "tratados pelo usuário", mesmo se estiverem fora de um bloco try/catch. Por isso, agora é necessário verificá-los explicitamente na janela Configurações de Exceção se você quiser que o depurador seja interrompido.

Na janela Configurações de Exceção (Depurar > Windows > Configurações de Exceção), expanda o nó de uma categoria de exceções (por exemplo, Exceções de Common Language Runtime, ou seja, exceções de .NET) e marque a caixa de seleção referente à exceção específica que você deseja capturar nessa categoria (por exemplo, System.NullReferenceException). Você também pode selecionar uma categoria inteira de exceções.

### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>No Windows, o Visual Studio pede para baixar a estrutura de destino do Unity
As Ferramentas do Visual Studio para Unity requerem o .NET Framework 3.5, que não está instalado por padrão no Windows 8 nem no 10. Para corrigir esse problema, siga as instruções para baixar e instalar o .NET Framework 3.5.

Ao usar o novo tempo de execução do Unity, versão de pacotes de direcionamento do .NET 4.6 e 4.7.1 também são necessários. É possível usar o instalador do VS2017 para instalá-los rapidamente (modificar sua instalação do VS2017, componentes individuais, categoria do .NET, selecionar todos os pacotes de direcionamento 4.x).

### <a name="assembly-reference-issues"></a>Problemas de referência de assembly
Se seu projeto consegue lidar com referências complexas ou se você quiser controlar melhor essa etapa de geração, use nossa [API](../cross-platform/customize-project-files-created-by-vstu.md) para manipular o conteúdo da solução ou do projeto gerado. Você também pode usar [arquivos de resposta](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) no seu projeto Unity, que serão processados para você.

### <a name="breakpoints-with-a-warning"></a>Pontos de interrupção com um aviso
Se o Visual Studio não conseguir encontrar um local de origem para um ponto de interrupção específico, você verá um aviso ao lado do ponto de interrupção. Verifique se o comportamento que você está usando está carregado e está sendo usado corretamente na cena atual do Unity.

### <a name="breakpoints-not-hit"></a>Pontos de interrupção não atingidos
Verifique se o comportamento que você está usando está carregado e está sendo usado corretamente na cena atual do Unity. Feche o Visual Studio e o Unity e exclua os arquivos gerados (*.csproj, *.sln) e toda a pasta Biblioteca.

### <a name="unable-to-attach"></a>Não é possível anexar
-   Tente desabilitar o antivírus temporariamente ou criar regras de exclusão para o VS e o Unity.
-   Tente desabilitar o firewall temporariamente ou criar regras para permitir a rede TCP/UDP entre o Unity e o VS.
-   Identificamos que programas, como o Team Viewer, estão interferindo na detecção do processo. Tente interromper temporariamente algum software adicional para ver se algo é alterado.
-   Não renomeie o executável principal do Unity, uma vez que o VSTU está monitorando apenas os processos de “Unity.exe”.

### <a name="unable-to-debug-android-players"></a>Não é possível depurar players Android
O multicast é usado para a detecção de player (que é o mecanismo padrão usado pelo Unity), mas depois disso, é usada uma conexão TCP regular para anexar o depurador. A fase de detecção é o principal problema para dispositivos Android.

O Wi-Fi é versátil, mas é muito lento em comparação com o USB devido à latência. Foi constatada uma falta de suporte adequado ao multicast para alguns roteadores ou dispositivos (a série Nexus é conhecida por isso).

O USB é bastante rápido para a depuração, e as Ferramentas do Visual Studio para Unity agora são capazes de detectar dispositivos USB e de se comunicar com o servidor adb para encaminhar corretamente as portas para depuração.

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrar do UnityVS para as Ferramentas do Visual Studio para Unity
 Caso esteja migrando do UnityVS para as Ferramentas do Visual Studio para Unity, será necessário gerar novas soluções do Visual Studio para os projetos do Unity.

##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Migrar um projeto do Unity do UnityVS 1.8 para as Ferramentas do Visual Studio para Unity 1.9

1.  Exclua a solução e os arquivos de projeto antigos do projeto do Unity. No diretório raiz do projeto do Unity, localize os arquivos .sln e .*proj do Visual Studio e exclua todos eles.

2.  Importe as Ferramentas do Visual Studio para Unity para o pacote do Unity no projeto do Unity. Para obter informações sobre como importar o pacote VSTU, consulte Configurar as Ferramentas do Visual Studio para Unity na página [Introdução](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md).

3.  Gerar novas soluções e arquivos de projeto. Caso deseje gerá-los neste momento, escolha **Ferramentas do Visual Studio** e **Gerar Arquivos de Projeto** no menu principal do Editor do Unity. Caso contrário, é possível ignorar essa etapa; as Ferramentas do Visual Studio para Unity gerarão os novos arquivos automaticamente quando você escolher **Ferramentas do Visual Studio** e **Abrir no Visual Studio**.

## <a name="known-issues"></a>Problemas Conhecidos
 Há problemas conhecidos nas Ferramentas do Visual Studio para Unity, decorrentes de como o depurador interage com a versão mais antiga do compilador C# do Unity. Estamos trabalhando para ajudar a corrigir esses problemas, mas, enquanto isso, você poderá enfrentar os seguintes problemas:

-   O Unity pode falhar durante a depuração.

-   O Unity pode congelar durante a depuração.

-   A intervenção ou saída de métodos pode se comportar incorretamente, especialmente em iteradores ou em instruções switch.

## <a name="reporting-errors"></a>Erros de relatório
 Ajude-nos a melhorar a qualidade das Ferramentas do Visual Studio para Unity enviando relatórios de erro quando ocorrerem falhas, congelamentos ou outros erros. Isso nos ajuda a investigar e corrigir problemas nas Ferramentas do Visual Studio para Unity. Obrigado!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Como relatar um erro quando o Visual Studio congela
 Há relatórios que indicam que, às vezes, o Visual Studio congela ao depurar com as Ferramentas do Visual Studio para Unity, mas precisamos de mais dados para entender esse problema. Ajude-nos a investigá-lo seguindo as etapas abaixo.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Para relatar que o Visual Studio congela durante a depuração com as Ferramentas do Visual Studio para Unity

*No Windows:*

1.  Abra uma nova instância do Visual Studio.

2.  Abra o diálogo Anexar ao Processo. Na nova instância do Visual Studio, escolha **Depurar** e **Anexar ao Processo** no menu principal.

3.  Anexe o depurador à instância congelada do Visual Studio. No diálogo **Anexar ao Processo**, selecione a instância congelada do Visual Studio na tabela **Processos Disponíveis** e, em seguida, escolha o botão **Anexar**.

4.  Pause o Depurador. Na nova instância do Visual Studio, no menu principal, escolha **Depurar**, **Interromper Tudo** ou apenas pressione **Ctrl + Alt + Break**.

5.  Crie um despejo de thread. Na janela Comando, insira o seguinte comando e pressione **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Talvez seja necessário tornar a janela **Comando** visível primeiro. No Visual Studio, escolha **Exibir**, **Outras Janelas**, **janela Comando** no menu principal.

*No Mac:*

1. Abra um terminal e obtenha o PID do Visual Studio para Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Inicie o depurador lldb:

    ```shell
    lldb
    ```

1. Anexe à instância do Visual Studio para Mac usando o PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Recupere o rastreamento de pilha de todos os threads:

    ```shell
    bt all
    ```

Por fim, envie o despejo de thread para [vstusp@microsoft.com](mailto:vstusp@microsoft.com), junto com uma descrição do que você estava fazendo quando o Visual Studio congelou.
