---
title: Solucionando problemas de VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73c754de72238671dd10235e792c43fb6d0a1b5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-vspackages"></a>Solucionando problemas de VSPackages
Estes são problemas comuns que você pode ter com o VSPackage e dicas para resolver os problemas.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Para solucionar problemas de um VSPackage que mantém o Visual Studio seja iniciado  
  
-   Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no modo de segurança.  
  
     Para iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no modo de segurança, em um prompt de comando, digite **devenv.exe /safemode**.  
  
     Durante esse processo não VSPackages são carregados exceto os VSPackages estão incluídos com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Para solucionar problemas de um VSPackage que não carregam  
  
1.  Certifique-se de que você está usando a raiz do registro no qual o VSPackage é registrado para ser executado, geralmente a raiz do registro experimental.  
  
     Para obter mais informações, consulte [a instância Experimental](../extensibility/the-experimental-instance.md).  
  
2.  Se o VSPackage destina-se para ser executado na raiz do registro experimental, certifique-se de que você está executando a versão experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Para executar a versão experimental, digite o seguinte em uma janela de comando: **devenv /rootsuffix exp**.  
  
3.  Verifique as entradas de registro de VSPackage.  
  
     Para obter mais informações, consulte [registrando VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) e [Gerenciando VSPackages](../extensibility/managing-vspackages.md).  
  
4.  Abra o **saída** janela da instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que falha ao carregar o VSPackage. Obter informações sobre por que o VSPackage falha podem ser exibidas na janela.  
  
    > [!NOTE]
    >  Se você estiver começando a versão experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inspecionar o ambiente de desenvolvimento integrado (IDE), o **saída** janela de ambas as versões.  
  
5.  Examine o log de atividades.  
  
     Para obter mais informações, consulte [como: usar o Log de atividades](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Para obter mais informações sobre exceções geradas pelo IDE, clique em **exceções** no **depurar** menu para habilitar as exceções. No **exceções** caixa de diálogo Selecionar os tipos de exceções que você deseja obter mais informações.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Para solucionar problemas de um VSPackage que não registrado  
  
1.  Certifique-se de que o assembly VSPackage reside em um local confiável. RegPkg não é possível registrar assemblies em um local não confiável ou parcialmente confiável, como um compartilhamento de rede na configuração de segurança do .net padrão. Embora um aviso é exibido sempre que um usuário cria um projeto em um local não confiável, a caixa de seleção "não mostrar esta mensagem novamente" pode evitar este aviso ocorra.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Para solucionar problemas de um comando que não é visível ou que gera um erro quando você clicar em um comando  
  
1.  Mesclar os comandos de menu novos ou alterados e aqueles já no IDE, digitando o seguinte no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Prompt de comando: **/rootsuffix devenv /setup Exp**.  
  
2.  Verifique se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] encontrará UI.dll para seu VSPackage.  
  
    1.  Encontre o CLSID do VSPackage na seção de pacotes do registro:  
  
         Studio HKLM\Software\Microsoft\Visual\\*\<versão >* \Packages  
  
    2.  Verifique se o caminho fornecido pelo subchave SatelliteDll está correto.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Para solucionar problemas de um VSPackage que se comporta de forma inesperada  
  
1.  Defina os pontos de interrupção no seu código.  
  
     Bons pontos de partida para depuração são o construtor e o método de inicialização. Você também pode definir pontos de interrupção na área que você deseja avaliar, como um comando de menu. Para habilitar pontos de interrupção, você deve executar sob o depurador.  
  
    1.  No menu **Projeto**, clique em **Propriedades**.  
  
    2.  Sobre o **páginas de propriedade** caixa de diálogo, selecione o **depurar** guia.  
  
    3.  No **argumentos de linha de comando** , digite o sufixo de raiz do ambiente de desenvolvimento que seu VSPackage destinos. Por exemplo, para selecionar a compilação experimental, digite: **RootSuffix Exp**.  
  
    4.  Sobre o **depurar** menu, clique em **iniciar depuração** ou pressione F5.  
  
        > [!NOTE]
        >  Se você estiver depurando um projeto, criar ou carregar uma instância existente do seu projeto agora.  
  
2.  Use o log de atividades.  
  
     Rastrear o comportamento de VSPackage gravando informações no log de atividades nos pontos-chave. Essa técnica é especialmente útil quando você executa um VSPackage em um ambiente comercial. Para obter mais informações, consulte [como: usar o Log de atividades](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Use os símbolos públicos.  
  
     Para melhorar a legibilidade durante a depuração, você pode anexar os símbolos do depurador.  
  
    1.  Do **Ferramentas/opções** menu, navegue até o **/símbolos de depuração** caixa de diálogo.  
  
    2.  Adicione esse **símbolo local do arquivo (. PDB)**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Para melhorar o desempenho, especifique uma pasta de cache de símbolo, por exemplo:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Para solucionar um VSPackage ausente ou uma de suas dependências  
  
1.  Para código gerenciado, certifique-se de que os caminhos de referência estão corretos.  
  
    1.  No menu **Projeto**, clique em **Propriedades**.  
  
    2.  Selecione o **referências** guia o **páginas de propriedade** caixa de diálogo e verifique se todos os caminhos estão corretos. Como alternativa, você pode usar o **Pesquisador de objetos** para procurar os objetos referenciados.  
  
         Para código gerenciado, você pode usar o [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) para exibir os detalhes de cargas de assembly com falha.  
  
2.  Para código não gerenciado, localize o CLSID do VSPackage no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nó de registro CLSID:  
  
     Studio HKLM\Software\Microsoft\Visual\\*\<versão >* \CLSID  
  
 Certifique-se de que a entrada InprocServer32 tem o caminho correto da dll VSPackage.  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)