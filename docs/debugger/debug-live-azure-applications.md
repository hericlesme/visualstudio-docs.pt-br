---
title: Depurar aplicativos ao vivo do Azure do ASP.NET - Visual Studio | Microsoft Docs
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger
ms.custom: mvc
ms.date: 03/16/2018
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
ms.openlocfilehash: d313dea17700d4e64d3156ee72ee15521111329b
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Depurar aplicativos ao vivo do Azure do ASP.NET usando o depurador do instantâneo

O depurador de instantâneo tira um instantâneo de seus aplicativos em produção quando executa código que você está interessado. Para instruir o depurador a tirar um instantâneo, defina snappoints e logpoints em seu código. O depurador permite ver exatamente o que deu errado sem afetar o tráfego do seu aplicativo de produção. O Depurador de Instantâneo pode ajudar a reduzir drasticamente o tempo que leva para resolver problemas que ocorrem em ambientes de produção.

Snappoints e logpoints são semelhantes aos pontos de interrupção, mas ao contrário de pontos de interrupção, snappoints não pare o aplicativo quando visitado. Normalmente, capturando um instantâneo em um snappoint leva 10 a 20 milissegundos. 

A coleção de instantâneos está disponível para os seguintes aplicativos Web em execução no Serviço de Aplicativo do Azure:

- Aplicativos ASP.NET em execução no .NET Framework 4.6.1 ou posterior.
- Aplicativos ASP.NET Core em execução no .NET Core 2.0 ou posterior no Windows.

Além disso, o depurador de instantâneo só está disponível para o Visual Studio 2017 Enterprise versão 15.5 ou superior e planos de serviço de aplicativo básico ou superior. 

Neste tutorial, você irá:

> [!div class="checklist"]
> * Iniciar o depurador do instantâneo
> * Definir um snappoint e exibir um instantâneo
> * Definir um logpoint

## <a name="start-the-snapshot-debugger"></a>Iniciar o depurador do instantâneo

1. Instalar [Visual Studio 2017 Enterprise versão 15,5](https://www.visualstudio.com/downloads/) ou posterior. Se você estiver atualizando de uma instalação anterior do Visual Studio de 2017, execute o instalador do Visual Studio e verifique o componente do depurador de instantâneo na carga de trabalho de desenvolvimento do ASP.NET e web.

2. Abra o projeto que você gostaria de depuração de instantâneo. 

    > [!IMPORTANT] 
    > A depuração de instantâneo, você precisa abrir o **mesma versão do código-fonte** que é publicada para o serviço de aplicativo do Azure. 

3. No Gerenciador de nuvem (**exibição > Cloud Explorer**), o serviço de aplicativo do Azure seu projeto é implantado e selecione **Anexar depurador de instantâneo**.

   ![Iniciar o depurador do instantâneo](../debugger/media/snapshot-launch.png)

    Na primeira vez que você selecionar **Anexar depurador de instantâneo**, será solicitado que você instale a extensão de site do depurador de instantâneo no seu serviço de aplicativo do Azure. Esta instalação requer uma reinicialização do seu serviço de aplicativo do Azure. 

   O Visual Studio agora está em modo de depuração de instantâneo.

    > [!NOTE]
    > A extensão de site do Application Insights também dá suporte à depuração de instantâneo. Se você encontrar uma mensagem de erro "site extensão desatualizado", consulte [solução de problemas e problemas conhecidos para a depuração de instantâneo](../debugger/debug-live-azure-apps-troubleshooting.md) para atualizar os detalhes.

   ![Modo de depuração de instantâneo](../debugger/media/snapshot-message.png)

   O **módulos** janela mostra quando todos os módulos de tem carregado para o serviço de aplicativo do Azure (escolha **depurar / Windows / módulos** para abrir essa janela).

   ![Verifique a janela módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Definir um snappoint

1. No editor de código, clique em medianiz esquerda ao lado de uma linha de código que você está interessado para definir um snappoint. Verifique se é um código que você sabe que será executado.

   ![Definir um snappoint](../debugger/media/snapshot-set-snappoint.png)

2. Clique em **iniciar coleta** para ativar o snappoint.  

   ![Ativar o snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Não é possível fazer ao exibir um instantâneo, mas você pode colocar várias snappoints em seu código para acompanhar a execução em linhas de código diferentes. Se você tiver vários snappoints em seu código, o depurador de instantâneo certifica-se de que os instantâneos correspondentes são da mesma sessão do usuário final. O depurador de instantâneo faz isso, mesmo se houver muitos usuários acessando o seu aplicativo.

## <a name="take-a-snapshot"></a>Tirar um instantâneo

Quando um snappoint é ativado, ele coletará um instantâneo sempre que executa a linha de código onde o snappoint é colocado. Essa execução pode ser causada por uma solicitação real em seu servidor. Para forçar o snappoint ocorrências, vá para o modo de exibição do navegador do seu site e executar quaisquer ações necessárias que fazer com que o snappoint seja atingido.

## <a name="inspect-snapshot-data"></a>Inspecionar dados de instantâneo

1. Quando o snappoint for atingido, um instantâneo é exibido na janela de ferramentas de diagnóstico. Para abrir essa janela, escolha **depurar / Windows / Mostrar ferramentas de diagnóstico**.

   ![Abra um snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Clique duas vezes em snappoint para abrir o instantâneo no editor de códigos.

   ![Inspecionar dados de instantâneo](../debugger/media/snapshot-inspect-data.png)

   Nessa exibição, você pode focalizar variáveis para exibir DataTips, use o **locais**, **observa**, e **pilha de chamadas** windows e também avaliar expressões.

    O site em si está ainda ativo e os usuários finais não são afetados. Apenas um instantâneo é capturado por snappoint por padrão: depois de um instantâneo é capturado o snappoint desativa. Se você deseja capturar outro instantâneo no snappoint, você pode ativar o snappoint novamente clicando **atualização coleção**.

Você também pode adicionar mais snappoints ao seu aplicativo e ligá-los com o **atualização coleção** botão.

**Precisa de ajuda?** Consulte o [problemas conhecidos e solução de problemas](../debugger/debug-live-azure-apps-troubleshooting.md) e [perguntas Frequentes de depuração de instantâneo](../debugger/debug-live-azure-apps-faq.md) páginas.

## <a name="set-a-conditional-snappoint"></a>Definir um snappoint condicional

Se você tiver dificuldades recriar um estado específico em seu aplicativo, considere se o uso de um snappoint condicional pode ajudar. Snappoints condicional ajuda a que evitar tirar um instantâneo, até que o aplicativo entra no estado desejado, como quando uma variável tem um valor específico que deseja inspecionar. Você pode definir condições de uso de expressões, filtros, ou contagens de ocorrências.

#### <a name="to-create-a-conditional-snappoint"></a>Para criar um snappoint condicional

1. Clique em um ícone de snappoint (a bola vazio) e escolha **configurações**.

   ![Escolha as configurações](../debugger/media/snapshot-snappoint-settings.png)

1. Na janela de configurações snappoint, digite uma expressão.

   ![Digite uma expressão](../debugger/media/snapshot-snappoint-conditions.png)

   Na ilustração anterior, o instantâneo é criado somente para o snappoint quando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Definir um logpoint

Além de gerar um instantâneo quando um snappoint for atingido, você também pode configurar um snappoint para registrar uma mensagem (ou seja, criar um logpoint). Você pode definir logpoints sem ter de reimplantar o aplicativo. Logpoints são executados virtualmente e fazer com que nenhum impacto ou efeitos colaterais para seu aplicativo em execução.

#### <a name="to-create-a-logpoint"></a>Para criar um logpoint

1. Clique em um ícone de snappoint (o hexágono azul) e escolha **configurações**.

1. Na janela de configurações snappoint, selecione **ações**.

    ![Criar um logpoint](../debugger/media/snapshot-logpoint.png)

1. No campo mensagem, você pode inserir a nova mensagem de log que você deseja registrar. Você também pode avaliar variáveis na mensagem de log, colocando-os entre chaves.

    Se você escolher **enviar para a janela de saída**, quando o logpoint é atingido, a mensagem é exibida na janela de ferramentas de diagnóstico.

    ![Dados de Logpoint na janela diagsession](../debugger/media/snapshot-logpoint-output.png)

    Se você escolher **enviar o log de aplicativo**, quando o logpoint for atingido, a mensagem é exibida em qualquer lugar que você pode ver as mensagens de `System.Diagnostics.Trace` (ou `ILogger` no núcleo do .NET), como [ideias de aplicativo](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como usar o depurador de instantâneo. Você talvez queira ler mais detalhes sobre esse recurso.

> [!div class="nextstepaction"]
> [Perguntas frequentes sobre depuração de instantâneos](../debugger/debug-live-azure-apps-faq.md)
