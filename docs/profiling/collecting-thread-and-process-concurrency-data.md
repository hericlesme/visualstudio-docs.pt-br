---
title: Coletando dados de simultaneidade do thread e do processo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 424675726dd91664923cde0a3a5ad5573d51b4d5
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34548319"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Coletar dados de simultaneidade de thread e do processo

O método de criação de perfil de simultaneidade das Ferramentas de Criação de Perfil do Visual Studio permite coletar dados de contenção de recursos que inclui informações sobre cada evento de sincronização que faz com que uma função no aplicativo analisado aguarde para obter acesso a um recurso.

É possível especificar o método de criação de perfil de simultaneidade usando um dos seguintes recursos:

- Na primeira página do Assistente de Criação de Perfil, clique em **Simultaneidade**
- Na página **Geral** da caixa de diálogo de propriedades da sessão de desempenho, clique em **Simultaneidade**.
- Na barra de ferramentas do **Gerenciador de Desempenho**, na lista **Método**, clique em **Simultaneidade**.

## <a name="common-tasks"></a>Tarefas comuns

É possível especificar outras opções na caixa de diálogo *Sessão de Desempenho***Páginas de Propriedades** da sessão de desempenho. Para abrir essa caixa de diálogo:

- No **Gerenciador de Desempenho**, clique com o botão direito do mouse no nome da sessão de desempenho e clique em **Propriedades**.

As tarefas na tabela a seguir descrevem as opções que podem ser especificadas na caixa de diálogo *Sessão de Desempenho***Páginas de Propriedades** quando você cria o perfil usando o método de simultaneidade.

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|Na página **Geral**, especifique detalhes de nomenclatura para o arquivo de dados de criação de perfil gerado (.vsp).|- [Como definir opções do nome do arquivo de dados de desempenho](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na página **Iniciar**, especifique o aplicativo a ser iniciado se você tiver vários projetos .exe na solução do seu código.|- [Como especificar o binário a iniciar](../profiling/how-to-specify-the-binary-to-start.md)|
|Na página **Interação de Camada**, adicione dados de chamada ADO.NET à execução de criação de perfil.|- [Coletar dados de interação entre camadas](../profiling/collecting-tier-interaction-data.md)|
|Na página **Contadores do Windows**, especifique um ou mais contadores de desempenho de sistema operacional para serem adicionados aos dados de criação de perfil como marcas.|- [Como coletar dados do contador do Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na página **Avançado**, especifique a versão do tempo de execução do .NET Framework a ter o perfil criado se seus módulos de aplicativo usarem várias versões. Por padrão, a primeira versão carregada é analisada.|- [Como especificar o tempo de execução do .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|