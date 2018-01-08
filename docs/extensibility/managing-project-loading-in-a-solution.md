---
title: "Ao carregar o projeto em uma solução de gerenciamento | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a2be2c75704646bab50f89377d960d44f6fa14f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="managing-project-loading-in-a-solution"></a>Gerenciando ao carregar o projeto em uma solução
Soluções do Visual Studio podem conter um número grande de projetos. O comportamento padrão do Visual Studio é carregar todos os projetos em uma solução no momento em que a solução é aberta e não permitir que o usuário acesse qualquer um dos projetos até que todos eles concluiu o carregamento. Quando o processo de carregamento do projeto irão durar mais de dois minutos, uma barra de progresso é exibida mostrando o número de projetos carregados e o número total de projetos. O usuário pode descarregar projetos enquanto estiver trabalhando em uma solução com vários projetos, mas esse procedimento apresenta algumas desvantagens: os projetos descarregados não são criados como parte de um comando recompilar solução e IntelliSense descrições dos tipos e membros de fechados projetos não são exibidos.  
  
 Os desenvolvedores podem reduzir os tempos de carregamento de solução e gerenciar o comportamento de carregamento por meio da criação de uma carga de solução Gerenciador de projeto. O Gerenciador de carga de solução pode definir outro projeto ao carregar as prioridades de projetos específicos ou tipos de projeto, certifique-se de que os projetos sejam carregados antes de iniciar uma compilação de plano de fundo, atrasar o carregamento de plano de fundo até que outras tarefas em segundo plano sejam concluídas e executar outras tarefas de gerenciamento de carga do projeto.  
  
## <a name="project-loading-priorities"></a>Carregando as prioridades de projeto  
 O Visual Studio define quatro prioridades de carregamento do projeto diferente:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>(o padrão): quando uma solução é aberta, projetos são carregados de forma assíncrona. Se esta prioridade é definida em um projeto descarregado depois que a solução já está aberta, o projeto será carregado no próximo ponto ocioso.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: quando uma solução é aberta, os projetos são carregados em segundo plano, permitindo que o usuário acessar os projetos que são carregados sem ter que aguardar até que todos os projetos são carregados.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projetos são carregados quando eles são acessados. Um projeto é acessado quando o usuário expande o nó do projeto no Gerenciador de soluções, quando um arquivo que pertence ao projeto é aberto quando a solução é aberto porque ele está na lista de documentos abertos (mantida no arquivo de opções de usuário da solução), ou quando outro projeto Isto é que está sendo carregado tem uma dependência no projeto. Esse tipo de projeto não é carregado automaticamente antes de iniciar um processo de compilação; o Gerenciador de carga de solução é responsável por garantir que todos os projetos necessários estão carregados. Esses projetos também devem ser carregados antes de iniciar um localizar/substituir em arquivos em toda a solução.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projetos não devem ser carregados, a menos que o usuário solicita explicitamente. Esse é o caso quando os projetos são descarregados explicitamente.  
  
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
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementando IVsSolutionLoadManager  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> método é chamado durante o processo de abertura da solução. Para implementar esse método, você deve usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> serviço para definir a prioridade de carga para o tipo de projeto que você deseja gerenciar. Por exemplo, o código a seguir define tipos de projeto c# para carregar em segundo plano:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> método é chamado quando o Visual Studio está sendo desligado ou quando um pacote diferente tiver assumido como o Gerenciador de carga de solução ativa chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> com o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriedade.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estratégias para diferentes tipos de Gerenciador de carga de solução  
 Você pode implementar gerenciadores de carga de solução de maneiras diferentes, dependendo dos tipos de soluções, que eles devem gerenciar.  
  
 Se o Gerenciador de carga de solução destina-se para gerenciar a solução de carregamento em geral, ele pode ser implementado como parte de um VSPackage. O pacote deve ser definido como autoload adicionando o <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> sobre o VSPackage com um valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. O Gerenciador de carga de solução, em seguida, pode ser ativado no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
> [!NOTE]
>  Para obter mais informações sobre pacotes autoloading, consulte [VSPackages carregar](../extensibility/loading-vspackages.md).  
  
 Como o Visual Studio reconhece somente o última solução Gerenciador de carga a ser ativado, gerenciadores de carga da solução geral sempre devem detectar se há um Gerenciador de carga existente antes de ativar a mesmos. Se chamar GetProperty() no serviço de solução para <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> retorna `null`, não há nenhum Gerenciador de carga de solução ativa. Se não retornar nulo, verifique se o objeto é o mesmo que o Gerenciador de carga de solução.  
  
 Se o Gerenciador de carga de solução destina-se para gerenciar somente alguns tipos de solução, o VSPackage pode assinar eventos de carga de solução (chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) e usar o manipulador de eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> para ativar o Gerenciador de carga de solução.  
  
 Se o Gerenciador de carga de solução deve gerenciar apenas as soluções específicas, as informações de ativação podem ser persistente como parte do arquivo de solução. Para fazer isso, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> para a seção de solução de pré-lançamento.  
  
 Gerenciadores de carga de solução específica devem desativar a mesmos no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> manipulador de eventos, para não entrar em conflito com outros gerenciadores de carga de solução.  
  
 Se você precisar de um Gerenciador de carga de solução somente para manter as prioridades de carga global de projeto (por exemplo, propriedades definidas em uma página de opções), você pode ativar o Gerenciador de carga de solução no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> manipulador de eventos, manter a configuração nas propriedades da solução, em seguida, Desative o Gerenciador de carga de solução.  
  
## <a name="handling-solution-load-events"></a>Manipulação de eventos de carga de solução  
 Para assinar eventos de carregamento de solução, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando você ativa o Gerenciador de carga de solução. Se você implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, você pode responder a eventos relacionados às prioridades de carregamento de projeto diferente.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Isso é disparado antes de uma solução é aberta. Você pode usá-lo para alterar o projeto de carregamento de prioridade para os projetos na solução.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Isso é disparado depois que a solução é completamente carregada, mas antes de plano de fundo projeto carregamento começa novamente. Por exemplo, um usuário pode ter acessado um projeto cuja prioridade de carga é LoadIfNeeded ou o Gerenciador de carga de solução pode ter alterado uma prioridade de carga do projeto para BackgroundLoad, que poderia iniciar um carregamento em segundo plano do projeto.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Isso é acionado depois que uma solução inicialmente totalmente carregada, se houver um Gerenciador de carga de solução ou não. Ele também será acionado após o carregamento em segundo plano ou demanda de carga sempre que a solução se tornar totalmente carregada. Ao mesmo tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> for reativado.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Isso é disparado antes do carregamento de um projeto (ou projetos). Para garantir que outros processos em segundo plano sejam concluídos antes dos projetos são carregados, defina `pfShouldDelayLoadToNextIdle` para **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Isso é disparado quando um lote de projetos está prestes a ser carregado. Se `fIsBackgroundIdleBatch` for true, os projetos devem ser carregados em segundo plano; se `fIsBackgroundIdleBatch` for falso, os projetos devem ser carregado de forma síncrona como resultado de uma solicitação de usuário, por exemplo se o usuário expande um projeto pendentes no Gerenciador de soluções. Você pode implementar esse trabalho caras que caso contrário, precisa ser feito em <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Isso é acionado depois que um lote de projetos foi carregado.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Detectar e gerenciar a solução e o carregamento do projeto  
 Para detectar o estado de carregamento de projetos e soluções, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> com os seguintes valores:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se a solução e todos os seus projetos forem carregados, caso contrário, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se um lote de projetos estão atualmente sendo carregados em segundo plano, caso contrário, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se um lote de projetos estão atualmente sendo carregados síncrona como resultado de um comando de usuário ou outros carregamento explícito, caso contrário, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` retorna `true` se a solução está atualmente sendo fechada, caso contrário, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` retorna `true` se uma solução está atualmente sendo aberta, caso contrário, `false`.  
  
 Você também pode garantir que os projetos e soluções são carregadas (independentemente de quais são as prioridades de carregamento do projeto) chamando um dos métodos a seguir:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: chamar esse método força os projetos em uma solução para carregar antes que o método retorna.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: chamar esse método força os projetos `guidProject` carregar antes que o método retorna.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: chamar esse método força o projeto no `guidProjectID` carregar antes que o método retorna.  
  
> [!NOTE]
>  . Por padrão somente os projetos que têm a demanda de carga e prioridades de carregamento em segundo plano são carregadas, mas se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> sinalizador é passado para o método, todos os projetos serão carregados, exceto aqueles que são marcados para carregar explicitamente.