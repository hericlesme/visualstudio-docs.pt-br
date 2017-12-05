---
title: "Otimizar o carregamento de soluções no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 08/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: 84989983-84bc-4f81-97a8-2131e3a25138
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.performancecenter
ms.technology: vs-ide-general
ms.openlocfilehash: 2102fc026b566c89108f0d74dcf604020653e358
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="optimize-solution-loading-in-visual-studio"></a>Otimizar o carregamento de soluções no Visual Studio
Muitas soluções contêm um grande número de projetos, o que afeta o tempo gasto para carregá-las. No entanto, em ambientes de equipe, os desenvolvedores normalmente trabalham em um subconjunto diferente desses projetos e não precisam carregar todos os projetos individuais.

O Visual Studio 2017 é compatível com o **carregamento da solução leve**. Quando o modo LSL (carregamento da solução leve) estiver habilitado, o Visual Studio 2017 carregará um pequeno subconjunto de projetos em vez de carregar todos os projetos em uma solução grande. A maioria das funcionalidades mais usadas do IDE funciona no modo LSL e ele fornece a capacidade de compilar, de pesquisar e de depurar a solução inteira. (O principal recurso não compatível com o modo LSL é editar e continuar).

> [!NOTE]
> Este conteúdo é aplicável ao Visual Studio 2017 Atualização 3

Para grandes soluções com mais de 30 projetos, o modo LSL normalmente carrega soluções duas vezes mais rápido (em média). Embora a maioria das funcionalidades do IDE funciona no modo LSL, algumas delas podem exigir que todos os projetos sejam carregados. Nesses casos, o Visual Studio carrega automaticamente a solução inteira para que você possa usar o recurso. Na pior das hipóteses, você carregará todos os projetos no modo leve. 

Se você usar um recurso do IDE em um projeto não carregado no momento, o Visual Studio carregará os projetos apropriados para você. Por exemplo, se você estiver tentando criar ou abrir um diagrama de classe de um projeto não aberto, o Visual Studio carregará automaticamente os projetos apropriados. A lista detalhada de recursos será mencionada nas seções a seguir.

As seções a seguir mostram como habilitar o carregamento da solução leve e também ajudará você a decidir se deve ou não habilitar o recurso.

## <a name="enable-or-disable-lightweight-solution-load"></a>Habilitar ou desabilitar a carga de solução leve

Você pode clicar com o botão direito do mouse no nome da solução no Gerenciador de Soluções e selecionar **Habilitar a Carga de Solução Leve**. Depois de selecionar a opção, você precisa fechar e reabrir a solução para ativar a carga de solução leve.

> [!NOTE]
> Etapas semelhantes aplicam-se para desabilitar o LSL. Para desabilitar o carregamento da solução leve, selecione **Desabilitar o Carregamento da Solução Leve** e, em seguida, feche e reabra a solução. 

![Gerenciador de Soluções](../ide/media/VSIDE_LSL_Solution_Setting.png)

## <a name="global_solution_load_settings"></a>Definir as configurações globais para o carregamento da solução leve

Você pode desabilitar globalmente ou configurar o LSL para todas as soluções escolhendo **Ferramentas > Opções > Projetos e Soluções**.

![Caixa de diálogo Opções de Ferramentas](../ide/media/VSIDE_LightweightSolutionLoad.png)

## <a name="how-does-lightweight-solution-load-work-behind-the-scenes"></a>Como funciona o carregamento da solução leve em segundo plano?

Quando você carrega a solução, o Visual Studio lembra quais projetos você abriu anteriormente e carrega apenas esses projetos. Todos os outros projetos permanecem visíveis no Gerenciador de Soluções, mas não são carregados. Depois de você expandir um projeto ou clicar com o botão direito do mouse em um projeto, o Visual Studio carregará o projeto de maneira automática. O carregamento automático de projetos normalmente demora menos de um segundo, mas pode demorar mais para alguns projetos.
No entanto, o Visual Studio habilita funcionalidades do IDE como pesquisar, depurar, compilar e controlar o código-fonte que funcionam na solução inteira. Por exemplo, você pode pesquisar em uma solução inteira, mesmo que apenas alguns projetos estejam carregados no modo leve. 

Ao expandir mais projetos, o Visual Studio se lembrará da lista de projetos expandidos. Ao reabrir uma solução, o Visual Studio carregará automaticamente os projetos expandidos anteriormente.

## <a name="visual-studio-prompts-developers-likely-to-see-significant-performance-gains"></a>O Visual Studio avisa os desenvolvedores que provavelmente obterão ganhos significativos de desempenho

Da telemetria do Visual Studio, as soluções grandes com mais de 30 projetos obtêm benefícios significativos no modo LSL. Consequentemente, avisamos os desenvolvedores com soluções grandes para experimentar o modo LSL. A maioria dos desenvolvedores que experimenta o LSL pela primeira vez acaba usando esse modo regularmente. 

Examinamos constantemente a telemetria de uso do Visual Studio para melhorar a heurística de modo a oferecer o modo LSL para desenvolvedores que podem conseguir mais benefícios. 

## <a name="visual-studio-makes-recommendations-to-turn-on-lightweight-solution-load-based-on-heuristics"></a>O Visual Studio faz recomendações para ativar o carregamento da solução leve com base em heurística

Por padrão, o Visual Studio ativa o LSL para usuários com maior probabilidade de obter benefícios com ele. Se você tiver várias soluções, o Visual Studio oferecerá modo LSL para soluções com maior probabilidade de obter ganhos de desempenho significativos. Se você selecionar a opção do modo leve **Permita que o Visual Studio decida** (opção padrão), o Visual Studio poderá abrir a solução no modo leve com base na heurística. Uma barra de mensagens indica se a solução está no modo leve. Quando a barra de mensagens aparecer, você terá a opção de saber mais ou atualizar as configurações.

![Janela pop-up](../ide/media/VSIDE_LSL_Popup.png)

## <a name="ide-features-fully-supported-in-lightweight-mode"></a>Funcionalidades do IDE totalmente compatíveis no modo leve

|Recurso|Compatível no modo leve?|
|-|-|-|
|IntelliSense|Sim|
|Pesquisar|Sim|
|Depuração|Sim|
|Build|Sim|
|Navegação de código (Ir para Definição e Localizar Todas as Referências)|Sim|
|CodeLens|Sim|
|Análise de código estático|Sim|
|Implantar e publicar|Sim|
|Adição e remoção de referências|Sim|
|Multiplataforma|Sim|
|IntelliTrace|Sim|
|Live Unit Testing|Sim|
|IntelliTest|Sim|
|Microsoft Fakes|Sim|
|Editar e continuar|Sem suporte|
|Teste de unidade|Requer o carregamento de projetos de teste seguidos por um build da solução|

## <a name="scenarios-in-which-lightweight-solution-loads-the-appropriate-projects-to-complete-the-operation"></a>Cenários em que a solução leve carrega os projetos apropriados para concluir a operação

Se você não estiver trabalhando em um projeto na solução, ele não será carregado no modo leve. Para algumas funcionalidades, projetos adicionais são carregados automaticamente para garantir a compatibilidade com o cenário do recurso. (Pretendemos minimizar essa lista de cenários.) Para esses cenários, o Visual Studio carrega os projetos automaticamente ou solicita que você carregue os projetos conforme necessário.

|Categoria|Problema|
|-|-|-|
|Teste de unidade|Os projetos não carregados no momento não aparecem na lista de projetos de teste dos assistentes “Criar IntelliTest” e “Criar Teste de Unidade”. </br>Você precisa carregar os projetos para o qual você deseja criar testes (você pode expandir o nó do projeto para carregar o projeto).|
|Diagramas de classe|Se você criar ou abrir um diagrama de classe de um projeto, o Visual Studio carregará automaticamente os projetos que são dependências diretas do projeto. </br>Se a solução inteira não for carregada, desligaremos a validação dos artefatos obsoletos referenciados por um diagrama de validação de dependência.|

## <a name="scenarios-in-which-lightweight-solution-loads-the-entire-solution"></a>Cenários em que a solução leve carrega a solução inteira 

Para algumas funcionalidades, o Visual Studio carrega automaticamente a solução inteira para garantir a compatibilidade com o cenário. Essa ação garante que você obtenha sempre a funcionalidade completa. Por exemplo, algumas operações do TFS podem exigir que a solução inteira seja carregada. Para fornecer a funcionalidade completa, o Visual Studio carregará a solução inteira.

|Categoria|Cenário|
|-|-|-|
|Comando SCC do TFS no nó da solução|Se um comando SCC for disparado no nó da solução (no Gerenciador de Soluções), o Visual Studio carregará automaticamente a solução inteira antes de concluir o comando.|
|Carregamento do projeto|Se a solução contiver projetos do .NET Core e compartilhados, o Visual Studio sempre carregará automaticamente esses projetos durante o carregamento inicial da solução em si. No momento, esses projetos não são compatíveis com o modo leve.|
|Gerenciador de configurações da solução|Se você usar o gerenciador de configurações da solução ou o build em lote, o Visual Studio carregará automaticamente a solução inteira para fornecer uma experiência completa.|
|Gerenciador de pacotes NuGet|Se você abrir a interface do usuário do gerenciador de pacotes do NuGet ou o console do gerenciador de pacotes do NuGet, o Visual Studio carregará automaticamente a solução inteira para fornecer uma experiência completa.|

## <a name="known-issues"></a>Problemas conhecidos

Existem alguns cenários que podem não funcionar no modo LSL e que exigem o carregamento de projetos adicionais ou da solução inteira. Estamos trabalhando ativamente para resolver esses casos. 

|Categoria|Problema|Solução alternativa|
|-|-|-|-|
|IntelliSense|O IntelliSense pode não ser atualizado após uma alteração de configuração (por exemplo, a alteração de um build de versão pela depuração e vice-versa). O impacto dependerá das diferenças do código devido à alteração de configuração.|Recarregue a solução após alterar a configuração.|
|Limitações de refatoração para projetos em C#/VB|Pode haver uma falha silenciosa nas correções de código que alteram os arquivos de projeto pela primeira vez.|Carregue projetos se precisar fazer correções no código dos arquivos desses projetos. O modo leve não faz correções em projetos não carregados.|
|Detecção de testes de unidade|Os testes detectados em projetos adiados não são executados quando um projeto é carregado manualmente.|Recompile o projeto para detectar os testes novamente e execute os testes selecionados novamente.|
|LUT (Live Unit Testing)|No modo LSL, você pode ver que o LUT não está ativado. Ele não está ativado porque o LUT precisa de um dos projetos de teste ao ser carregado.|Carregue qualquer projeto de teste para ativar o Live Unit Testing para a solução.|
|Pesquisa do Gerenciador de Soluções|1.    A pesquisa do Gerenciador de Soluções no modo LSL não pesquisa nos arquivos e não há resultados de progressão (isto é, somente arquivos são exibidos na árvore de pesquisa, mas não classes, métodos, etc.).</br>2.    Todos os arquivos pertencentes a um projeto são mostrados como uma lista plana em vez de um modo de exibição de árvore. Quando os arquivos pertencem a uma pasta de um projeto, mostramos o caminho relativo do arquivo, em vez de apenas o nome do arquivo no modo de exibição de pesquisa.</br>Não há nenhum menu de contexto para os itens de arquivo na exibição de pesquisa.|Carregue a solução inteira em um modo não LSL para usar a pesquisa tradicional do Gerenciador de Soluções.</br>Você também pode usar a pesquisa do IDE do Visual Studio.|
|Pesquisador de Objetos para projetos C++|O Pesquisador de Objetos mostra referências de assembly/WinMD apenas para os projetos carregados.|Carregue projetos dos quais você deseja ver informações no Pesquisador de Objetos.|

> [!Note]
> Graças aos nossos parceiros, extensões populares, incluindo o Resharper, também funcionam bem com o carregamento da solução leve.

Estamos empolgados com as inovações para otimizar o desempenho do tempo do carregamento da solução para desenvolvedores. Por ser um recurso novo, estamos observando ativamente os comentários dos clientes e resolvendo os problemas conhecidos. Aguardamos os seus comentários. Envie um email para a equipe de otimização do carregamento de solução do Visual Studio no endereço lslsupport@microsoft.com

## <a name="see-also"></a>Consulte também
[Dicas e truques de desempenho do Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
