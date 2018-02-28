---
title: Depurar aplicativos ao vivo do Azure do ASP.NET - Visual Studio | Microsoft Docs
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 5317c06dc5ff6515627e562d576785c2ff25a98a
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Depurar aplicativos ao vivo do Azure do ASP.NET usando o depurador do instantâneo

O depurador de instantâneo tira um instantâneo de seus aplicativos em produção quando executa código que você está interessado. Para instruir o depurador a tirar um instantâneo, defina snappoints e logpoints em seu código. O depurador permite ver exatamente o que deu errado sem afetar o tráfego do seu aplicativo de produção. O Depurador de Instantâneo pode ajudar a reduzir drasticamente o tempo que leva para resolver problemas que ocorrem em ambientes de produção.

Snappoints e logpoints são semelhantes aos pontos de interrupção. Ao contrário de pontos de interrupção, snappoints não pare o aplicativo quando visitado. Normalmente, capturando um instantâneo em um snappoint leva 10 a 20 milissegundos. 

A coleção de instantâneos está disponível para os seguintes aplicativos Web em execução no Serviço de Aplicativo do Azure:

- Aplicativos ASP.NET em execução no .NET Framework 4.6.1 ou posterior.
- Aplicativos ASP.NET Core em execução no .NET Core 2.0 ou posterior no Windows.

Além disso, o depurador de instantâneo só está disponível para o Visual Studio 2017 Enterprise versão 15.5 ou superior e planos de serviço de aplicativo básico ou superior. 

## <a name="start-the-snapshot-debugger"></a>Iniciar o depurador do instantâneo

1. Instalar [Visual Studio 2017 Enterprise versão 15,5](https://www.visualstudio.com/downloads/) ou posterior. Se você estiver atualizando de uma instalação anterior do Visual Studio de 2017, execute o instalador do Visual Studio e verifique o componente do depurador de instantâneo na carga de trabalho de desenvolvimento do ASP.NET e web.

2. Abra o projeto que você gostaria de depuração de instantâneo. 

    > [!IMPORTANT] 
    > A depuração de instantâneo, é necessário abrir o **mesma versão do código-fonte** que é publicada para o serviço de aplicativo do Azure. 

3. No Gerenciador de nuvem (selecione **exibição > Cloud Explorer**), o serviço de aplicativo do Azure seu projeto é implantado para clique com botão direito e selecione **Anexar depurador de instantâneo** para iniciar o depurador do instantâneo.

   ![Iniciar o depurador do instantâneo](../debugger/media/snapshot-launch.png "iniciar o depurador do instantâneo")

    Na primeira vez que você selecionar **Anexar depurador de instantâneo**, você precisará instalar a extensão de site do depurador de instantâneo em seu serviço de aplicativo do Azure. Esta instalação requer uma reinicialização do seu serviço de aplicativo do Azure. 

   O Visual Studio agora está em modo de depuração de instantâneo.

    > [!NOTE]
    > A extensão de site do Application Insights também dá suporte à depuração de instantâneo. Se você encontrar uma mensagem de erro "site extensão desatualizado", consulte [solução de problemas e problemas conhecidos para a depuração de instantâneo](../debugger/debug-live-azure-apps-troubleshooting.md) para atualizar os detalhes.

   ![Modo de depuração de instantâneo](../debugger/media/snapshot-message.png "modo de depuração de instantâneo")

   O **módulos** janela mostra quando todos os módulos de tem carregado para o serviço de aplicativo do Azure (escolha **depurar / Windows / módulos** para abrir essa janela).

   ![Verifique a janela módulos](../debugger/media/snapshot-modules.png "Verifique a janela módulos")

## <a name="set-a-snappoint"></a>Definir um snappoint

1. No editor de código, clique em medianiz esquerda ao lado de uma linha de código que você está interessado para definir um snappoint. Verifique se é um código que você sabe que será executado.

   ![Definir um snappoint](../debugger/media/snapshot-set-snappoint.png "definir um snappoint")

2. Clique em **iniciar coleta** para ativar o snappoint.  

   ![Ativar o snappoint](../debugger/media/snapshot-start-collection.png "ativar o snappoint")

    > [!TIP]
    > Não é possível fazer ao exibir um instantâneo, mas você pode colocar várias snappoints em seu código para acompanhar a execução em linhas de código diferentes. Se você tiver vários snappoints em seu código, o depurador de instantâneo garante que os instantâneos correspondentes são da mesma sessão do usuário final, mesmo se houver vários usuários acessando o seu aplicativo.

## <a name="take-a-snapshot"></a>Tirar um instantâneo

Quando um snappoint é ativado, ele coletará um instantâneo sempre que a linha de código onde o snappoint é colocado é executada. Essa execução pode ser causada por uma solicitação real em seu servidor. Para forçar o snappoint para ocorrências, você também pode ir para a exibição do navegador de seu site e execute que as ações necessárias que fazer com que o snappoint seja atingido.

## <a name="inspect-snapshot-data"></a>Inspecionar dados de instantâneo

1. Quando o snappoint for atingido, um instantâneo é exibido na janela de ferramentas de diagnóstico. Escolha **depurar / Windows / Mostrar ferramentas de diagnóstico** para abrir essa janela.

   ![Abra um snappoint](../debugger/media/snapshot-diagsession-window.png "abrir um snappoint")

1. Clique duas vezes em snappoint para abrir o instantâneo no editor de códigos.

   ![Inspecionar dados de instantâneo](../debugger/media/snapshot-inspect-data.png "inspecionar dados de instantâneo")

   Nessa exibição, você pode focalizar variáveis para exibir DataTips, use o **locais**, **observa**, e **pilha de chamadas** windows e também avaliar expressões.

    O site ainda é dinâmica e os usuários finais não são afetados. Apenas um instantâneo é capturado por snappoint por padrão: depois de um instantâneo é capturado o snappoint desativa. Se você deseja capturar outro instantâneo no snappoint, você pode ativar o snappoint novamente clicando **atualização coleção**.

Você também pode adicionar mais snappoints ao seu aplicativo e ligá-los com o **atualização coleção** botão.

**Precisa de ajuda?** Consulte o [problemas conhecidos e solução de problemas](../debugger/debug-live-azure-apps-troubleshooting.md) e [perguntas Frequentes de depuração de instantâneo](../debugger/debug-live-azure-apps-faq.md) páginas.

## <a name="set-a-conditional-snappoint"></a>Definir um snappoint condicional

Se você tiver dificuldades recriar um estado específico em seu aplicativo, considere se o uso de um snappoint condicional pode ajudar. Você pode usar snappoints condicional para evitar tirar um instantâneo até que o aplicativo entra no estado desejado, como quando uma variável tem um valor específico você está interessado. Você pode definir condições de uso de expressões, filtros, ou contagens de ocorrências.

#### <a name="to-create-a-conditional-snappoint"></a>Para criar um snappoint condicional

1. Clique em um ícone de snappoint (a bola vazio) e escolha **configurações**.

   ![Escolha configurações](../debugger/media/snapshot-snappoint-settings.png "escolher configurações")

1. Na janela de configurações snappoint, digite uma expressão.

   ![Digite uma expressão](../debugger/media/snapshot-snappoint-conditions.png "digite uma expressão")

   Na ilustração anterior, o instantâneo é criado somente para o snappoint quando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Definir um logpoint

Além de gerar um instantâneo quando um snappoint for atingido, você também pode configurar um snappoint para registrar uma mensagem (ou seja, criar um logpoint). Você pode definir logpoints sem ter de reimplantar o aplicativo. Logpoints são executados virtualmente e fazer com que nenhum impacto ou efeitos colaterais para seu aplicativo em execução.

#### <a name="to-create-a-logpoint"></a>Para criar um logpoint

1. Clique em um ícone de snappoint (o hexágono azul) e escolha **configurações**.

1. Na janela de configurações snappoint, selecione **ações**.

    ![Criar um logpoint](../debugger/media/snapshot-logpoint.png "criar um logpoint")

1. No campo mensagem, você pode inserir a nova mensagem de log que você deseja registrar. Você também pode avaliar variáveis na mensagem de log, colocando-os entre chaves.

    Se você escolher **enviar para a janela de saída**, quando o logpoint é atingido, a mensagem é exibida na janela de ferramentas de diagnóstico.

    ![Dados de Logpoint na janela diagsession](../debugger/media/snapshot-logpoint-output.png "Logpoint dados na janela diagsession")

    Se você escolher **enviar o log de aplicativo**, quando o logpoint for atingido, a mensagem é exibida em qualquer lugar que você pode ver as mensagens de `System.Diagnostics.Trace` (ou `ILogger` no núcleo do .NET), como [ideias de aplicativo](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Próximas etapas

- Para saber como inspecionar variáveis ao exibir um instantâneo, consulte [tour pelos recursos do depurador](../debugger/debugger-feature-tour.md).
- Exibição de [perguntas Frequentes de depuração de instantâneo](../debugger/debug-live-azure-apps-faq.md).
- Exibição [solução de problemas e problemas conhecidos para a depuração de instantâneo](../debugger/debug-live-azure-apps-troubleshooting.md).
- Se você quiser exibir instantâneos no Application Insights quando seu aplicativo atinge uma exceção, você pode fazer isso. Para obter mais informações, consulte [depurar instantâneos de exceções em aplicativos .NET](/azure/application-insights/app-insights-snapshot-debugger). Application Insights oferece suporte a aplicativos de serviço de malha além do serviço de aplicativo do Azure.
