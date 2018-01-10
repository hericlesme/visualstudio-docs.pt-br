---
title: "Criação de perfil de desempenho de aplicativos do SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
ms.assetid: 61ae02e7-3f37-4230-bae1-54a498c2fae8
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 70c058f6c930b9eb58cf0518d3418ccedcf083b4
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="profiling-the-performance-of-sharepoint-applications"></a>Criando o perfil do desempenho de aplicativos do SharePoint
  Se seus aplicativos do SharePoint estiverem lento ou ineficiente, você pode usar os recursos de criação de perfil no Visual Studio para identificar código problemática e outros elementos. Usando a recurso de teste de carga, você pode determinar como um aplicativo do SharePoint executa sob carga excessiva, como quando muitos usuários acessam o aplicativo simultaneamente. Executando testes de desempenho na web, você pode medir o desempenho do aplicativo na web. Usando testes de IU codificados, você pode verificar se o aplicativo do SharePoint inteiro, incluindo sua interface de usuário, funciona corretamente. Quando você usar esses testes juntos, eles podem ajudá-lo a identificar problemas de desempenho antes de implantar seu aplicativo.  
  
## <a name="profiling-tools-overview"></a>Visão Geral das Ferramentas de Criação de Perfil  
 Criação de perfil se refere ao processo de observando e registrando o comportamento de desempenho do seu aplicativo conforme ele é executado. Por seu aplicativo de criação de perfil, você pode descobrir problemas como afunilamentos, código ineficiente e problemas de alocação de memória, o que fazer com que aplicativos sejam executados lentamente ou usar muita memória. Por exemplo, você pode usar a criação de perfil para identificar pontos de acesso no seu código, que são segmentos de código que são chamados com frequência e podem diminuir o desempenho geral do seu aplicativo. Depois de identificar pontos de acesso, geralmente você pode otimizar ou eliminá-las.  
  
 Você pode usar várias ferramentas de criação de perfil no ambiente de desenvolvimento integrado (IDE) para identificar e localizar esses tipos de problemas de desempenho. Essas ferramentas funcionam da mesma forma para projetos do SharePoint como para outros tipos de projetos do Visual Studio. O Assistente de criação de perfil de desempenho de ferramentas leva você através da criação de uma sessão de desempenho que usa os testes que você especificar. Uma sessão de desempenho é um conjunto de dados de configuração que são usados para coletar informações sobre o desempenho de um aplicativo, junto com os resultados de um ou mais fluxos de criação de perfil. Sessões de desempenho são armazenadas na pasta do projeto, e você pode exibi-los em **Performance Explorer**. Para obter mais informações, consulte [Noções Básicas sobre Métodos de Coleta de Desempenho](/visualstudio/profiling/understanding-performance-collection-methods).  
  
 Depois de criar e executar uma análise de perfil em seu aplicativo, um relatório fornece detalhes sobre o desempenho. Este relatório pode incluir itens como um gráfico de uso da CPU de tempo, uma pilha de chamadas de função hierárquico ou uma árvore de chamada. O conteúdo exato do relatório pode variar, dependendo do tipo de teste que você executa, como amostragem ou instrumentação. Para obter mais informações, consulte [visão geral do relatório de ferramentas de criação de perfil](http://go.microsoft.com/fwlink/?LinkId=224689).  
  
## <a name="performance-session-process"></a>Processo da Sessão de Desempenho  
 Para criar o perfil de um aplicativo, você deve iniciar usando o Assistente de criação de perfil de desempenho de ferramentas para criar uma sessão de desempenho. Na barra de menus, escolha **analisar**, **iniciar o Assistente de desempenho**. Ao concluir o assistente, você pode inserir as informações necessárias para a sessão de desempenho, como o método de perfil que você quer e o aplicativo cujo perfil você deseja. Para obter mais informações, consulte [como: criar o perfil de um Site ou aplicativo Web usando o Assistente de desempenho](http://go.microsoft.com/fwlink/?LinkId=224692). Como alternativa, você pode usar opções de linha de comando para configurar e executar uma sessão de desempenho. Para obter mais informações, consulte [usando a criação de perfil ferramentas da linha de comando](http://go.microsoft.com/fwlink/?LinkId=224703). Se você deseja configurar todos os aspectos de uma sessão de desempenho manualmente, consulte [como: criar dos sessões de desempenho manualmente com as ferramentas de criação de perfil](http://go.microsoft.com/fwlink/?LinkId=224691). Você também pode criar uma sessão de desempenho de um teste de unidade, além de **resultados do teste** janela, abrindo o menu de atalho para o teste de unidade e, em seguida, escolhendo **criar sessão de desempenho**.  
  
 Depois de configurar uma sessão de desempenho, a configuração de sessão é salvo, o servidor está configurado para fornecer dados de criação de perfil e o aplicativo é executado. Como você usa o aplicativo, dados de desempenho são gravados em um arquivo de log. Sessões de desempenho são listadas na **Performance Explorer** sob o **destinos** pasta. Após a conclusão de uma sessão de desempenho, o relatório aparece no **relatórios** pasta **Performance Explorer**. Para exibir o relatório, abra-o em **Performance Explorer**. Para exibir ou configurar as propriedades de uma sessão de desempenho, abra o menu de atalho em **Performance Explorer**e, em seguida, escolha **propriedades**. Para obter mais informações sobre propriedades específicas de uma sessão de desempenho, consulte [Configurando sessões de desempenho para as ferramentas de criação de perfil](http://go.microsoft.com/fwlink/?LinkId=224694). Para obter informações sobre como interpretar os resultados de uma sessão de desempenho, consulte [analisando dados de ferramentas de criação de perfil](http://go.microsoft.com/fwlink/?LinkId=224704).  
  
## <a name="stress-testing"></a>Teste de Estresse  
 Você pode analisar o desempenho da carga de seus aplicativos com a criação de testes de carga e testes de desempenho na web no Visual Studio Ultimate. Quando você cria um teste de carga no Visual Studio, você pode especificar uma combinação de fatores, chamado de um cenário, para testar o aplicativo em. Esses fatores incluem o padrão de carga, modelo de combinação de teste, mistura de teste, mistura de rede e combinação de navegadores da web. Cenários de teste de carga podem incluir testes de unidade e testes de desempenho na web.  
  
 Figura 1: Exemplo de resultados de teste de carga  
  
 ![Modo de exibição de gráficos de execução de teste de carga](../sharepoint/media/load-webgraphs.png "exibição de gráficos de execução de teste de carga")  
  
 Testes de desempenho Web simular como um usuário final pode interagir com um aplicativo do SharePoint. Você pode criar testes de desempenho web gravando solicitações HTTP em uma sessão de navegador ou usando o **gravador de testes de desempenho Web**. As solicitações da web aparecem no **Editor de testes de desempenho Web** após a sessão do navegador. Em seguida, você pode depurar os resultados de **Visualizador de resultados de teste de desempenho Web**. Você pode criar manualmente os testes de desempenho da web usando o **Editor de testes de desempenho Web**.  
  
## <a name="testing-user-interfaces"></a>Testando Interfaces de Usuário  
 Testes de IU codificados unidade automaticamente seu aplicativo do SharePoint por meio de sua interface de usuário (UI). Esses testes abrangem os controles de interface do usuário, como botões e menus para verificar que eles funcionem corretamente. Esse tipo de teste é particularmente útil se a validação ou outra lógica é executada na interface de usuário, como uma página da web. Você também pode usar testes de IU codificados para automatizar testes manuais. Criação de codificados testes de interface do usuário para seus aplicativos do SharePoint da mesma forma como você cria testes para outros tipos de aplicativos. Para obter mais informações, consulte [testando aplicativos do SharePoint 2010 com testes de IU codificados](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Instruções passo a passo: criando o perfil de um aplicativo do SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Demonstra como executar uma análise de perfil de amostragem em um aplicativo do SharePoint.|  
|[Realizar um teste de desempenho no aplicativo antes do lançamento](https://www.visualstudio.com/docs/test/performance-testing/run-performance-tests-app-before-release)|Descreve como criar testes de carga que ajudarão a aplicativos do teste de estresse do SharePoint.|  
|[Efetuar teste de unidade em seu código](/visualstudio/test/unit-test-your-code)|Descreve como localizar erros lógicos em seu código usando testes de unidade.|  
|[Testando os aplicativos do SharePoint 2010 com testes de IU codificados](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)|Descreve como testar a interface do usuário dos aplicativos do SharePoint.|  
  
## <a name="see-also"></a>Consulte também

[Compilando e depurando soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
[Melhorar a qualidade do código](/visualstudio/test/improve-code-quality)