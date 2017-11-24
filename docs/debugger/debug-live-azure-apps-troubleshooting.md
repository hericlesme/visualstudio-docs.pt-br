---
title: "Problemas conhecidos e solução de problemas para depuração de instantâneo | Microsoft Docs"
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e32587a7aac6e2595f35488ad057995c04f4b
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2017
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problemas conhecidos e solução de problemas para instantâneo de depuração no Visual Studio

Se as etapas descritas neste tópico não resolverem seu problema, entre em contato com snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: Snappoint não ativar

Se você vir um ícone de aviso ![ícone de aviso Snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "ícone de aviso Snappoint") com seu snappoint em vez de no ícone snappoint regular, em seguida, o snappoint não está ativado.

![Snappoint não ativar](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint não ativar")

Siga estas etapas:

1. Verifique se que você tem a mesma versão do código-fonte que foi usado para criar e implantar seu app.isua1. Verifique se que você está carregando os símbolos corretos para sua implantação. Para fazer isso, exibir o **módulos** janela durante a depuração de instantâneo e verifique se a coluna do arquivo de símbolo mostra um arquivo. PDB carregado para o módulo que você está depurando. Observe que o depurador de instantâneo tentará baixar automaticamente e usar os símbolos para sua implantação.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: Os símbolos não são carregados quando abrir um instantâneo

Se você vir a seguinte janela, símbolos não foram carregado.

![Símbolos não carregar](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "símbolos não são carregados.")

Siga estas etapas:

- Clique o **alterar configurações de símbolo...** vincular nesta página. No **depuração > símbolos** configurações, adicionar um diretório de cache de símbolo. Reinicie a depuração de instantâneo depois que o caminho do símbolo foi definido.

   Os símbolos ou arquivos. PDB, disponíveis em seu projeto devem corresponder a implantação do serviço de aplicativo. A maioria das implantações (implantação por meio do Visual Studio, CI/CD com VSTS ou Kudu, etc.) serão publicar os arquivos de símbolo ao longo de seu serviço de aplicativo. Definir o diretório de cache de símbolo permite que o Visual Studio para usar esses símbolos.

   ![Configurações de símbolo](../debugger/media/snapshot-troubleshooting-symbol-settings.png "configurações de símbolo")

- Como alternativa, se sua organização usa um servidor de símbolo ou descarta os símbolos em um caminho diferente, use as configurações de símbolo para carregar os símbolos corretos para sua implantação.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: não consigo ver a opção "Anexar o depurador de instantâneo" no Gerenciador de nuvem

Siga estas etapas:

- Verifique se que o componente do depurador de instantâneo está instalado. Abra o instalador do Visual Studio e verifique o **instantâneo depurador** componente na carga de trabalho do Azure.
- Verifique se há suporte para seu aplicativo. No momento, somente o ASP.NET (4.6.1+) e há suporte para aplicativos ASP.NET Core (2.0 e posteriores) implantados para os serviços de aplicativo do Azure.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: vejo apenas limitadas instantâneos nas ferramentas de diagnóstico

![Throttled snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "limitadas snappoint")

Siga estas etapas:

- Instantâneos ocupam muito pouca memória, mas têm um encargo de confirmação. Se o depurador de instantâneo detecta que o servidor está sob carga pesada de memória, ele não entrará em instantâneos. Você pode excluir instantâneos já capturados por interromper a sessão do depurador de instantâneo e tente novamente.

## <a name="known-issues"></a>Problemas conhecidos

- Atualmente não há suporte para a depuração de instantâneo com vários clientes do Visual Studio com o mesmo serviço de aplicativo.
- Otimizações de IL Roslyn não têm suporte total em projetos do ASP.NET Core. Para alguns projetos do ASP.NET Core, você não poderá ver algumas variáveis ou usar algumas variáveis em instruções condicionais. 
- Variáveis especiais, como *$FUNCTION* ou *$CALLER*, não pode ser avaliada em instruções condicionais ou logpoints para projetos do ASP.NET Core.
- Depuração de instantâneo não funciona em serviços de aplicativos que têm [Cache Local](https://docs.microsoft.com/en-us/azure/app-service/app-service-local-cache) ativado.
- Atualmente, não há suporte para depuração de aplicativos de API de instantâneo.

## <a name="see-also"></a>Consulte também

[Depurando no Visual Studio](../debugger/index.md)  
[Depurar aplicativos do ASP.NET ao vivo usando o depurador do instantâneo](../debugger/debug-live-azure-applications.md)  
[Perguntas frequentes sobre depuração de instantâneos](../debugger/debug-live-azure-apps-faq.md)  
