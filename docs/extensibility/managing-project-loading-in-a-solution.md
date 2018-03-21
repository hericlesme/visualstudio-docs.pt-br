---
title: "Ao carregar o projeto em uma solução de gerenciamento | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2dbbb8ddcf574f2e3db81ce63db257e21ff88839
ms.sourcegitcommit: a80e7ef2f0a0f6d906a44f4d696aeb208bc1ad70
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2018
---
# <a name="managing-project-loading-in-a-solution"></a>Gerenciando ao carregar o projeto em uma solução
Soluções do Visual Studio podem conter um número grande de projetos. O comportamento padrão do Visual Studio é carregar todos os projetos em uma solução no momento em que a solução é aberta e não permitir que o usuário acesse qualquer um dos projetos até que todos eles concluiu o carregamento. Quando o processo de carregamento do projeto irão durar mais de dois minutos, uma barra de progresso é exibida mostrando o número de projetos carregados e o número total de projetos. O usuário pode descarregar projetos enquanto estiver trabalhando em uma solução com vários projetos, mas esse procedimento apresenta algumas desvantagens: os projetos descarregados não são criados como parte de um comando recompilar solução e IntelliSense descrições dos tipos e membros de fechados projetos não são exibidos.  
  
 Os desenvolvedores podem reduzir os tempos de carregamento de solução e gerenciar o comportamento de carregamento por meio da criação de uma carga de solução Gerenciador de projeto. O Gerenciador de carga de solução Certifique-se de que os projetos sejam carregados antes de iniciar uma compilação de plano de fundo, atrasar o carregamento de plano de fundo até que outras tarefas em segundo plano sejam concluídas e executar outras tarefas de gerenciamento de carga do projeto.  
  
## <a name="creating-a-solution-load-manager"></a>Criando uma carga de solução manager  
 Os desenvolvedores podem criar Gerenciador de uma carga de solução implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e informando que o Visual Studio que o Gerenciador de carga de solução está ativo.  
  
#### <a name="activating-a-solution-load-manager"></a>Ativando um Gerenciador de carga de solução  
 O Visual Studio permite que apenas um Gerenciador de carga de solução em um determinado momento, portanto você deve informar o Visual Studio quando você deseja ativar sua carga de solução gerenciador. Se um Gerenciador de carga segunda solução é ativado mais tarde, o Gerenciador de solução de carga será desconectado.  
  
 Você deve obter o <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> de serviço e defina o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriedade:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> método é chamado quando o Visual Studio está sendo desligado ou quando um pacote diferente tiver assumido como o Gerenciador de carga de solução ativa chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> com o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriedade.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estratégias para diferentes tipos de Gerenciador de carga de solução  
 Você pode implementar gerenciadores de carga de solução de maneiras diferentes, dependendo dos tipos de soluções, que eles devem gerenciar.  
  
 Se o Gerenciador de carga de solução destina-se para gerenciar a solução de carregamento em geral, ele pode ser implementado como parte de um VSPackage. O pacote deve ser definido como autoload adicionando o <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> sobre o VSPackage com um valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. O Gerenciador de carga de solução, em seguida, pode ser ativado no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
> [!NOTE]
>  Para obter mais informações sobre pacotes autoloading, consulte [VSPackages carregar](../extensibility/loading-vspackages.md).  
  
 Como o Visual Studio reconhece somente o última solução Gerenciador de carga a ser ativado, gerenciadores de carga da solução geral sempre devem detectar se há um Gerenciador de carga existente antes de ativar a mesmos. Se chamar GetProperty() no serviço de solução para <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> retorna `null`, não há nenhum Gerenciador de carga de solução ativa. Se não retornar nulo, verifique se o objeto é o mesmo que o Gerenciador de carga de solução.  
  
 Se o Gerenciador de carga de solução destina-se para gerenciar somente alguns tipos de solução, o VSPackage pode assinar eventos de carga de solução (chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) e usar o manipulador de eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> para ativar o Gerenciador de carga de solução.  
  
 Se o Gerenciador de carga de solução deve gerenciar apenas as soluções específicas, as informações de ativação podem ser persistente como parte do arquivo de solução chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> para a seção de solução de pré-lançamento.  
  
 Gerenciadores de carga de solução específica devem desativar a mesmos no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> manipulador de eventos, para não entrar em conflito com outros gerenciadores de carga de solução.  
  
 Se você precisar de um Gerenciador de carga de solução somente para persistir as propriedades de projeto global de carga (por exemplo, propriedades definidas em uma página de opções), você pode ativar o Gerenciador de carga de solução no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> manipulador de eventos, manter a configuração nas propriedades da solução, em seguida, Desative o Gerenciador de carga de solução.  
  
## <a name="handling-solution-load-events"></a>Manipulação de eventos de carga de solução  
 Para assinar eventos de carregamento de solução, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando você ativa o Gerenciador de carga de solução. Se você implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, você pode responder a eventos relacionados ao carregar propriedades de projeto diferente.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Este evento é disparado antes de uma solução é aberta.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Esse evento é acionado depois que a solução é completamente carregada, mas antes de plano de fundo projeto carregamento começa novamente.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Esse evento é acionado depois que uma solução inicialmente totalmente carregada, se ou não há um Gerenciador de carga de solução. Ele também será acionado após o carregamento em segundo plano ou demanda de carga sempre que a solução se tornar totalmente carregada. Ao mesmo tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> for reativado.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Este evento é disparado antes do carregamento de um projeto (ou projetos). Para garantir que outros processos em segundo plano sejam concluídos antes dos projetos são carregados, defina `pfShouldDelayLoadToNextIdle` para **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Esse evento é acionado quando um lote de projetos está prestes a ser carregado. Se `fIsBackgroundIdleBatch` for true, os projetos devem ser carregados em segundo plano; se `fIsBackgroundIdleBatch` for falso, os projetos devem ser carregado de forma síncrona como resultado de uma solicitação de usuário, por exemplo se o usuário expande um projeto pendentes no Gerenciador de soluções. Você pode manipular esse evento para fazer o trabalho caro que outra forma precisaria ser feito em <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Esse evento é acionado depois que um lote de projetos foi carregado.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Detectar e gerenciar a solução e o carregamento do projeto  
 Para detectar o estado de carregamento de projetos e soluções, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> com os seguintes valores:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se a solução e todos os seus projetos forem carregados, caso contrário, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se um lote de projetos está atualmente sendo carregado em segundo plano, caso contrário, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se um lote de projetos está atualmente sendo carregado sincronicamente como resultado de um comando de usuário ou outros carregamento explícito, caso contrário, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` retorna `true` se a solução está atualmente sendo fechada, caso contrário, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` retorna `true` se uma solução está atualmente sendo aberta, caso contrário, `false`.  
  
 Você também pode garantir que os projetos e soluções são carregadas chamando um dos métodos a seguir:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: chamar esse método força os projetos em uma solução para carregar antes que o método retorna.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: chamar esse método força os projetos `guidProject` carregar antes que o método retorna.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: chamar esse método força o projeto no `guidProjectID` carregar antes que o método retorna.  
