---
title: Recursos do IntelliTrace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 01515701b6aeecc1166551c6376bfd6823e73976
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="intellitrace-features"></a>funcionalidades do IntelliTrace

Você pode usar o IntelliTrace para registrar eventos e chamadas de método do aplicativo, que permite que você examine seu estado (pilha de chamadas e valores de variáveis locais) em diferentes pontos de execução. Basta iniciar a depuração normalmente - IntelliTrace é ativado por padrão e você pode ver as informações de IntelliTrace está gravando no novo **ferramentas de diagnóstico** janela sob o **eventos** guia. Selecione um evento e clique em **Ativar depuração histórica** para ver a pilha de chamadas e locais registrados para este evento.

Para obter uma descrição passo a passo, consulte [passo a passo: usando o IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

O IntelliTrace está disponível na edição Enterprise do Visual Studio, mas não nas edições do Visual Studio Professional ou da comunidade.

Para confirmar que o IntelliTrace está ligado, abra o **Ferramentas > Opções > IntelliTrace** página de opções. **Habilitar o IntelliTrace** devem ser verificados por padrão.

> [!NOTE]
> O escopo de todas as configurações de **IntelliTrace** página de opções é o Visual Studio como um todo, soluções ou projetos individuais não. Uma alteração nessas configurações se aplica a todas as instâncias do Visual Studio, a depuração de todas as sessões e todos os projetos ou soluções.

## <a name="ChooseEvents"></a> Escolha os eventos que registros do IntelliTrace

Você pode ativar ou desativar a gravação de eventos do IntelliTrace específicos.

Se você estiver depurando, pare a depuração. Vá para **Ferramentas > Opções > IntelliTrace > eventos do IntelliTrace**. Escolha os eventos que você deseja que o IntelliTrace para registrar.

## <a name="Snapshots"></a> Coletar eventos e instantâneos

Isso não é habilitado por padrão, mas IntelliTrace pode capturar instantâneos de seu aplicativo em todos os eventos de etapa de ponto de interrupção e o depurador e você pode exibir instantâneos essas políticas em uma sessão de depuração histórica. Um instantâneo fornece uma exibição do seu estado de aplicativo completo. Para habilitar a captura de instantâneos, vá para **Ferramentas > Opções > IntelliTrace > geral**e selecione **IntelliTrace eventos e instantâneos**. Para obter mais informações, consulte [exibir instantâneos usando IntelliTrace etapa-back](../debugger/how-to-use-intellitrace-step-back.md)

Instantâneos estão disponíveis no 2017 de Enterprise do Visual Studio versão 15.5 e superior e requer a atualização de aniversário do Windows 10 ou superior.  Para aplicativos .NET Core e ASP.NET Core, a versão do Visual Studio Enterprise de 2017 visualização 15.7 1 é necessário.

## <a name="GoingFurther"></a> Coletar eventos do IntelliTrace e informações de chamadas

Isso não é habilitado por padrão, mas o IntelliTrace pode registrar as chamadas de método juntamente com eventos. Para habilitar a coleta do método chamadas acessem **Ferramentas > Opções > IntelliTrace > geral**e selecione **eventos do IntelliTrace e informações de chamadas**.

Informações de chamada não estão atualmente disponíveis para aplicativos .NET Core e ASP.NET Core. 

Isso lhe permite ver o histórico de pilha de chamada e etapa para trás para frente e chamadas em seu código. IntelliTrace registra os dados, como nomes de método, pontos de entrada e saída do método e determinados valores de parâmetros e valores de retorno.

> [!TIP]
> Essa opção não é habilitada por padrão porque ela adiciona uma sobrecarga considerável. Não apenas o IntelliTrace precisa interceptar todas as chamadas de método que faz com que seu aplicativo, mas ela também precisa lidar com um conjunto maior de dados quando se trata de mostrá-la na tela ou persisti-los para o disco.
>
> Você pode reduzir a sobrecarga de desempenho, restringindo a lista de eventos que registros do IntelliTrace e manter o número de módulos que você está coletando mínimo. Para obter mais informações, consulte [controle quanto chamar informações registros do IntelliTrace](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Exibir a navegação de uso

Você pode usar a medianiz de navegação que aparece à esquerda da janela de código. Se você não vir a medianiz de navegação, vá para **Ferramentas > Opções > IntelliTrace > Avançado**e selecione **exibir exibir a navegação em modo de depuração**.

Exibir a navegação permite que você mova para frente e para trás por meio de chamadas de método e eventos no modo de depuração histórico. Para obter mais informações sobre depuração histórica, consulte [depuração histórica](../debugger/historical-debugging.md). Ele tem um número de comandos:

|||
|-|-|
|**Definir o contexto do depurador aqui**|Defina o contexto de depuração para o período de chamada onde ele aparece.<br /><br /> Esse ícone é exibido apenas na pilha de chamadas atual.|
|**Retornar ao local de chamada**|Mova o ponteiro e o contexto de depuração para onde a função atual foi chamada.<br /><br /> Se você estiver no modo de depuração ao vivo, este comando ativa a depuração histórica. Se você navegar de volta para a interrupção da execução original, depuração histórica está desativado e depuração dinâmica está ativada.|
|**Ir para chamada anterior ou evento do IntelliTrace**|Mova o ponteiro e o contexto de depuração de volta para a chamada anterior ou o evento.<br /><br /> Se você estiver no modo de depuração ao vivo, este comando ativa a depuração histórica.|
|**Entrar**|Passar para a função selecionada no momento.<br /><br /> Este comando está disponível somente quando você estiver no modo de depuração histórica.|
|**Ir para próxima chamada ou evento do IntelliTrace**|Mova o ponteiro e o contexto de depuração para a próxima chamada ou evento para qual IntelliTrace dados existem.<br /><br /> Este comando está disponível somente quando você estiver no modo de depuração histórica.|
|**Ir para modo dinâmico**|Retornar ao modo de depuração dinâmica.|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>Pesquise uma linha ou um método no IntelliTrace

Você pode pesquisar métodos somente quando as informações de chamada de método foi habilitadas. Você pode pesquisar o histórico do IntelliTrace para uma linha específica ou um método. Enquanto o depurador a execução é suspensa, clique dentro do corpo da função para ver o menu de contexto e clique em **pesquisa para esta linha no IntelliTrace** ou **pesquisa para este método no IntelliTrace**.

### <a name="ControlCallData"></a> Controlar a quantidade de registros de chamada informações IntelliTrace

Por padrão o IntelliTrace registra informações para todos os módulos usados pela sua solução. Você pode definir o IntelliTrace para informações de registro chamada somente para os módulos que lhe interessam. Em **Ferramentas > Opções > IntelliTrace > módulos**, você pode especificar os módulos para incluir ou módulos a serem excluídos do IntelliTrace. IntelliTrace irá coletar apenas os eventos que tenham sido originados dos módulos que você especificou, e as chamadas de método que ocorreram dentro de módulos que lhe interessam.

Para adicionar vários módulos, use o caractere curinga * no início ou no final da cadeia de caracteres. Para nomes de módulos, use nomes de arquivos, e não nomes de assembly. Caminhos de arquivo não são aceitos.

Tente manter o número de módulos em um mínimo. Você obtém um desempenho melhor porque há menos dados a serem coletados. Você também obtém menos ruído na interface de usuário porque há menos dados para percorrer.

## <a name="SaveSession"></a> Salvar dados do IntelliTrace para arquivo

Você pode salvar os dados coletados IntelliTrace vai **Depurar > IntelliTrace > Salvar a sessão do IntelliTrace** enquanto você está depurando e o aplicativo está em um estado de interrupção. O item de menu está desativado e você não poderá salvar os dados do que IntelliTrace coletou se o aplicativo ainda está em execução ou interromper a depuração.

Você pode configurar o IntelliTrace para salvar um arquivo automaticamente acessando **Ferramentas > Opções > IntelliTrace > Avançado** e selecionando **gravações de repositório IntelliTrace neste diretório**. Você também pode configurar um tamanho de conjunto para o arquivo gerado, o que faz com que o IntelliTrace gravar dados mais antigos quando ele ficar sem espaço. Visual Studio cria dois arquivos para cada sessão do IntelliTrace quando eles são salvos automaticamente e o processo de hospedagem (vshost.exe) do Visual Studio está ativado.

> [!TIP]
> Para economizar espaço em disco, desative a salvar arquivos automaticamente quando você não precisa mais deles. Quaisquer arquivos existentes não serão excluídos. Você sempre pode salvar em arquivo sob demanda no menu de contexto.

Quando você salva dados do IntelliTrace para arquivo, você pode obter um arquivo. itrace de cada processo que IntelliTrace coletado de. Em seguida, você pode abrir o arquivo. itrace no Visual Studio indo para **arquivo > Abrir > arquivo** e selecionando o arquivo. itrace na caixa de diálogo Abrir arquivo. Para obter mais informações, consulte [usando IntelliTrace dados salvo](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Blogs

[IntelliTrace no Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)

[Instruções passo a passo de depuração dinâmica usando o IntelliTrace no Visual Studio 2015 (Editor de texto)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)

[Instruções passo a passo de depuração dinâmica usando o IntelliTrace no Visual Studio 2015 (sociedade Social)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)

[IntelliTrace no Visual Studio Enterprise 2015 agora oferece suporte à anexação!](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)

[Coletar dados de um serviço do windows usando o coletor IntelliTrace independente](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)

[Editar o plano de coleta do IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)

[TraceSource personalizados e depuração usando o IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)

[Execução do coletor IntelliTrace independente e Pools de aplicativos em contas do Active Directory](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)

## <a name="forums"></a>Fóruns

[Depurador do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)

## <a name="videos"></a>Vídeos

[Experiência do IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[A depuração histórica com o IntelliTrace no Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
