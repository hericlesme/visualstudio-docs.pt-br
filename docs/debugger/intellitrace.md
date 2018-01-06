---
title: IntelliTrace | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: "135"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bb0018e97cdbacc5e16e9591a0d480d509e1a9f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="intellitrace"></a>IntelliTrace
Você pode passar menos tempo depurar seu aplicativo quando você usar o IntelliTrace para registrar e rastrear o histórico de execução do seu código. Você pode localizar erros facilmente como IntelliTrace permite que você:  
  
-   Registrar eventos específicos  
  
     Examinar o código relacionado, dados que aparecem no **locais** durante eventos do depurador e informações de chamada de função  
  
-   Depurar erros que são difíceis de reproduzir ou que acontecem na implantação  
  
 Você pode usar o IntelliTrace na edição Enterprise do Visual Studio (mas não nas edições Professional ou comunidade).  
  
## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?  
  
|||  
|-|-|  
|**Depure o aplicativo com o IntelliTrace:**<br /><br /> -Mostre após eventos.<br />-Mostrar-me chamar informações com eventos passados.<br />-Salve minha sessão do IntelliTrace.<br />-Controle os dados que coleta do IntelliTrace.|-   [Passo a passo: Usando o IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [Recursos do IntelliTrace](../debugger/intellitrace-features.md)<br />-   [Depuração histórica](../debugger/historical-debugging.md)<br />-   [Instantâneos de modo de exibição usando o IntelliTrace etapa-back](../debugger/how-to-use-intellitrace-step-back.md)|  
|**Coletar dados do IntelliTrace durante uma sessão de teste no Test Manager**|-   [Coletar mais dados de diagnóstico em testes manuais](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests)|  
|**Coletar dados do IntelliTrace de aplicativos implantados**|-   [Usar o coletor autônomo do IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Inicie a depuração de um arquivo de log do IntelliTrace (arquivo. itrace).**|-   [Usando os dados salvos do IntelliTrace](../debugger/using-saved-intellitrace-data.md)|  
  
##  <a name="IntelliTraceSupport"></a>Quais aplicativos podem depurar com o IntelliTrace?  
  
|||  
|-|-|  
|**Com suporte**|-Aplicativos Visual Basic e Visual c# que usam o .NET Framework 2.0 ou versões posteriores.<br />     É possível depurar a maioria dos aplicativos, inclusive ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 e aplicativos de 64 bits.<br />     Para depurar aplicativos do SharePoint com o IntelliTrace, consulte [passo a passo: depurando um aplicativo do SharePoint, usando o IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br />     Para depurar aplicativos do Microsoft Azure com o IntelliTrace, consulte [depuração de um serviço de nuvem publicado com o Visual Studio e o IntelliTrace](/azure/vs-azure-tools-intellitrace-debug-published-cloud-services).|  
|**Suporte limitado**|-.NET core e ASP.NET Core aplicativos com suporte apenas para eventos de<br />-Aplicativos F # em uma base experimental<br />-Aplicativos da Windows Store Windows com suporte apenas para eventos de|  
|**Sem suporte**|-C++, outros idiomas e script<br />-Serviços do Windows, Silverlight, Xbox, ou [!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)] aplicativos|  
  
> [!NOTE]
>  Se você quiser depurar um processo que já está em execução, você pode coletar apenas eventos do IntelliTrace (nenhuma informação de chamada). Você pode anexar a um processo de 32 bits ou 64 bits na máquina local. Eventos que ocorrem antes de anexar ao processo não são coletados.
  
##  <a name="IntelliTraceVSTraditional"></a>Por que a depuração com o IntelliTrace?  
 Tradicional ou *live* depuração mostra somente do aplicativo atual estado, com dados limitada sobre os eventos anteriores. Você ter inferir esses eventos com base no estado atual do aplicativo, ou você precisa recriar esses eventos, execute novamente o seu aplicativo.  
  
 O IntelliTrace expande esta experiência tradicional de depuração ao registrar eventos específicos e os dados nesses pontos de tempo. Isso lhe permite ver o que aconteceu em seu aplicativo sem reiniciá-lo, especialmente se você passe onde está o bug. O IntelliTrace é ativado por padrão durante a depuração tradicional e coleta dados automaticamente e de forma invisível. Isso permite que você alterne facilmente entre a depuração tradicional e a depuração do IntelliTrace para consultar as informações registradas. Consulte [funcionalidades do IntelliTrace](../debugger/intellitrace-features.md) e [quais dados IntelliTrace coletar?](#WhatData)  
  
 O IntelliTrace também pode ajudá-lo a depurar erros que são difíceis de reproduzir ou que ocorrem na implantação. Você pode coletar dados do IntelliTrace e salvá-los em um arquivo de log do IntelliTrace (arquivo .iTrace). Um arquivo .iTrace contém detalhes sobre exceções, eventos de desempenho, solicitações da Web, dados de teste, threads, módulos e outras informações do sistema. Você pode abrir este arquivo no Visual Studio Enterprise, selecione um item e iniciar a depuração com o IntelliTrace. Assim que você vá para qualquer evento no arquivo e ver os detalhes específicos sobre o seu aplicativo no momento.  
  
 Você pode salvar dados do IntelliTrace a partir destas fontes:  
  
-   Uma sessão do IntelliTrace no Visual Studio Enterprise de 2017, o Visual Studio 2015 Enterprise ou versões anteriores do Visual Studio Ultimate.  
  
-   Uma sessão de teste no Microsoft Test Manager  
  
-   Aplicativos Web em ASP.NET hospedados no IIS ou aplicativos SharePoint 2010 e SharePoint 2013 em execução na implantação quando você usa o Agente de Monitoramento da Microsoft, sozinhos ou com o System Center 2012. Consulte [usar o coletor autônomo do IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) e [monitorando com o Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).  
  
 Estes são alguns exemplos de como o IntelliTrace pode ajudar na depuração:  
  
-   Seu aplicativo corrompeu um arquivo de dados, mas você não souber onde esse evento ocorreu.  
  
     Sem o IntelliTrace, que examinar o código para localizar todos os acessos de arquivo possíveis, colocar pontos de interrupção nos acessos e execute novamente o aplicativo para localizar onde o problema ocorreu. Com o IntelliTrace, você pode ver todos os eventos de acesso a arquivos coletados e detalhes específicos sobre o seu aplicativo quando cada evento ocorreu.  
  
-   Uma exceção ocorre.  
  
     Sem o IntelliTrace, você receberá uma mensagem sobre uma exceção, mas você não tiver a quantidade de informações sobre os eventos que conduziram à exceção. Você pode examinar a pilha de chamadas para ver a cadeia de chamadas que conduziram à exceção, mas não é possível ver a sequência de eventos que ocorreram durante as chamadas. Com o IntelliTrace, você pode examinar os eventos que ocorreram antes da exceção.  
  
-   Seu aplicativo falha em um computador de teste, mas é executado com êxito em um computador de desenvolvimento.  
  
     Você pode coletar dados do IntelliTrace do Microsoft Test Manager, salvar os dados em um arquivo .iTrace e anexar esse arquivo a um item de trabalho do Team Foundation Server para investigação posterior. Consulte [coletar mais dados de diagnóstico em testes manuais](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests) e [usar salva dados do IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
-   Um bug ou a falha ocorre em um aplicativo implantado.  
  
     Para aplicativos baseados no Azure da Microsoft, você pode configurar a coleta de dados do IntelliTrace, antes de publicar o aplicativo. Enquanto seu aplicativo é executado, o IntelliTrace salva dados em um arquivo. itrace. Consulte [depurar um serviço de nuvem publicado com o IntelliTrace e o Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).  
  
     Para aplicativos Web em ASP.NET hospedados no IIS 7.0, 7.5 e 8.0 e aplicativos SharePoint 2010 ou SharePoint 2013, use o Agente de Monitoramento da Microsoft sozinho ou com o System Center 2012 para salvar dados do IntelliTrace em um arquivo .iTrace.  
  
     Isso é útil quando você deseja diagnosticar problemas com os aplicativos durante a implantação. Consulte [usar o coletor autônomo do IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
##  <a name="WhatData"></a>Quais dados o IntelliTrace coletar?  
 **Coletar informações de evento**  
  
 Por padrão, o IntelliTrace registra somente os eventos do IntelliTrace: depurador eventos, exceções, os eventos do .NET Framework e outros eventos do sistema que podem ajudá-lo com a depuração. Você pode escolher os tipos de eventos do IntelliTrace que deseja coletar, exceto para eventos do depurador e exceções, os quais são coletados sempre. Consulte [funcionalidades do IntelliTrace](../debugger/intellitrace-features.md).  
  
-   **Eventos do depurador**  
  
     O IntelliTrace sempre registra eventos que acontecem no depurador do Visual Studio. Por exemplo, a partir de seu aplicativo é um evento de depurador. Outros eventos do depurador estão interrompendo eventos, o que fazer com que seu aplicativo para interromper a execução. Por exemplo, seu programa atinge um ponto de interrupção, atinge um tracepoint ou executa um **etapa** comando.  

     Por padrão, para ajudá-lo com o desempenho, IntelliTrace não Registre cada valor possível para um evento do depurador. Em vez de isso, ele registra estes valores:  
  
    -   Valores de **locais** janela. Manter o **locais** janela aberta para ver esses valores.  
  
    -   Valores no **Autos** somente se de janela a **Autos** janela está aberta  
  
    -   Valores em DataTips que surgem quando você move o ponteiro do mouse sobre uma variável na janela de origem para ver seu valor. O IntelliTrace não coleta valores em DataTips fixados.  

    Quando eventos do IntelliTrace e instantâneos de modo estiver habilitado, o IntelliTrace entrará em um instantâneo do processo do aplicativo em cada depurador **ponto de interrupção** e **etapa** eventos. Isso registrará os valores de **locais**, **Autos**, e **inspecionar** windows, independentemente se as janelas são abertas ou não. Valores em qualquer dicas de dados fixo também serão coletados. 
  
-   **Exceções**  
  
     O IntelliTrace registra o tipo e a mensagem de exceção para estes tipos de exceções:  
  
    -   Exceções tratadas onde a exceção é gerada e capturada  
  
    -   Exceções sem tratamento  
  
-   **Eventos do .NET framework**  
  
     Por padrão, o IntelliTrace registra os eventos mais comuns do .NET Framework. Por exemplo:  
  
    -   Para um evento de marcar caixa de seleção, o IntelliTrace coleta o estado e o texto da caixa de seleção.  
  
-   **Eventos de aplicativo do SharePoint 2010 e SharePoint 2013**  
  
     Você pode registrar eventos de perfil de usuário e um subconjunto de eventos do ULS (Sistema de Registro Unificado) para os aplicativos SharePoint 2010 e 2013 que são executados fora do Visual Studio. Você pode salvar esses eventos em um arquivo de .iTrace. Requer o Visual Studio Enterprise de 2017, o Visual Studio Enterprise 2015, uma versão anterior do Visual Studio Ultimate, ou [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) em execução em **rastreamento** modo.  
  
     Ao abrir o arquivo .iTrace, insira uma identificação de correlação do SharePoint para localizar a solicitação da Web correspondente, exibir os eventos registrados e iniciar a depuração de um evento específico. Se o arquivo contiver exceções sem tratamento, você poderá escolher uma identificação de correlação para iniciar a depuração de uma exceção.  
  
     Consulte:  
  
    -   [Usar o coletor autônomo do IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
    -   [Usar dados salvos do IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
    -   [Instruções passo a passo: depurando um aplicativo do SharePoint usando o IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)  
 
 **Captura de instantâneos**
 
 Você pode configurar o IntelliTrace para capturar instantâneos em cada ponto de interrupção e o evento de etapa do depurador. IntelliTrace registra o estado do aplicativo completo em cada instantâneo, que permite exibir variáveis complexos e avaliar expressões.

 Consulte [exibir instantâneos usando IntelliTrace etapa-back](../debugger/how-to-use-intellitrace-step-back.md).

 **Coletar informações de chamada de função**  
  
 Você pode configurar o IntelliTrace para coletar informações de chamada para funções. Essas informações permitem que você veja um histórico da pilha de chamadas e permitem que você percorra para frente e para trás as chamadas no código. Para cada chamada de função, o IntelliTrace registra estes dados:  
  
-   Nome da função  
  
-   Valores de tipos de dados primitivos passados como parâmetros em pontos de entrada de função e retornados em pontos de saída de função  
  
-   Valores de propriedades automáticas quando elas são lidas ou alteradas  
  
-   Ponteiros para objetos filhos de primeiro nível, mas não seus valores diferentes caso eles fossem nulos ou não  
  
> [!NOTE]
>  O IntelliTrace coleta somente os 256 primeiros objetos em matrizes e os 256 primeiros caracteres para cadeias de caracteres.  
  
 Consulte [inspecionar o seu aplicativo com depuração histórica](../debugger/historical-debugging-inspect-app.md).
  
 **Coletar informações de módulo**  
  
 Para controlar a quantidade de informações de chamadas que o IntelliTrace coleta, especifique somente os módulos que interessem a você. Isso pode ajudar a melhorar o desempenho do aplicativo durante a coleta. Consulte a seção [controlar a quantidade de informações coleta do IntelliTrace](../debugger/intellitrace-features.md#ControlCallData) em recursos do IntelliTrace.  
  
##  <a name="AffectPerformance"></a>Será IntelliTrace desacelerar meu aplicativo?  
 Por padrão, o IntelliTrace coleta dados somente para eventos do IntelliTrace selecionados. Isso pode ou não pode diminuir seu aplicativo, dependendo da estrutura e a organização do seu código. Por exemplo, se o IntelliTrace registra um evento com frequência, isso pode retardar o aplicativo. Ele também pode fazer você considerar a refatoração de seu aplicativo.  
  
 Coleta de informações de chamada pode diminuir seu aplicativo significativamente. Ela também pode aumentar o tamanho de qualquer arquivo de log do IntelliTrace (arquivos .iTrace) que você possa estar salvando em disco. Para minimizar esses efeitos, colete informações de chamada somente para os módulos desejados.  Para alterar o tamanho máximo dos arquivos. itrace, vá para **ferramentas**, **opções**, **IntelliTrace**, **avançado**. 
  
## <a name="in-this-section"></a>Nesta seção  
 [Recursos do IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Incluir dados de rastreamento de diagnóstico com que sejam difíceis de reproduzir](/devops-test-docs/test_notintoc/including-diagnostic-trace-data-with-bugs-that-are-difficult-to-reproduce)  
  
 [Diagnosticar problemas após a implantação](../debugger/diagnose-problems-after-deployment.md)  
  
 [Usar dados salvos do IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Blogs  
 [O Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>Fóruns  
 [Diagnóstico do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)