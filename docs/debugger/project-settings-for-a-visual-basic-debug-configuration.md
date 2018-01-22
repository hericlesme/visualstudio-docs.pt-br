---
title: "Configurações do projeto para uma configuração de depuração do Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a9d9b9c5cee3dc69698320af77a7cc909b344a2d
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2018
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Definições do projeto para uma configuração de depuração do Visual Basic
Você pode alterar as configurações de projeto para um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] configuração de depuração no **páginas de propriedade** janela, conforme discutido em [configurações Debug e Release](../debugger/how-to-set-debug-and-release-configurations.md). As tabelas a seguir mostram onde localizar configurações relacionadas a depuração no **páginas de propriedade** janela.  
  
> [!WARNING]
>  Este tópico não se aplica a aplicativos UWP. Consulte [iniciar uma sessão de depuração (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Guia Depurar  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|**Configuração**|Define o modo para compilar o aplicativo. Escolha entre **ativa (depuração)**, **depurar**, **versão**, **todas as configurações de**.|  
|**Iniciar ação**|Esse grupo de controles especifica a ação que ocorrerá quando você escolhe Iniciar do menu Depurar.<br /><br /> -   **Iniciar projeto** é o padrão e inicia o projeto de inicialização para depuração. <br />-   **Iniciar programa externo** permite que você inicie e anexe a um programa que não faz parte de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Iniciar navegador na URL** permite depurar um aplicativo da Web.|  
|**Argumentos de linha de comando**|Especifica argumentos de linha de comando para o programa ser depurado. O nome do comando é o nome do programa especificado em Iniciar programa externo. Se Iniciar Ação for definida para iniciar URL, os argumentos de linha de comando serão ignorados.|  
|**Diretório de trabalho**|Especifica o diretório de trabalho do programa que está sendo depurado. No [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], o diretório de trabalho é o diretório a partir do qual o aplicativo é iniciado. O diretório de trabalho padrão é \bin\Debug ou \bin\Release., dependendo da configuração atual.|  
|**Use um computador remoto**|Quando a caixa de seleção está marcada, a depuração remota é habilitada. Na caixa de texto, você pode digitar o nome de um computador remoto onde o aplicativo será executado para fins de depuração ou um [nome do servidor Msvsmon](../debugger/remote-debugging.md). O local do EXE no computador remoto é especificado pela propriedade Caminho da Saída na guia Compilação. O local deve ser um diretório compartilhável no computador remoto.|  
|**Depuração de código não gerenciado**|Permite depurar chamadas para código Win32 nativo (não gerenciado) a partir do seu aplicativo gerenciado. Isso tem o mesmo efeito que selecionar Misto como Tipo de Depurador em um projeto do [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].|  
|**Depuração de SQL Server**|Permite depuração de objetos de banco de dados do SQL Server.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Guia Compilar: pressione o botão Opções de Compilação Avançadas  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|**Habilitar otimizações**|Essa opção deve estar desmarcada. A otimização faz o código que é realmente executado ser diferente do código-fonte visto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e, portanto, dificulta a depuração. Se o código estiver otimizado, os símbolos não serão carregados por padrão ao depurar com Apenas Meu Código.|  
|**Gerar informações de depuração**|Definida por padrão nas versões de depuração e lançamento, essa configuração (equivalente à opção /debug do compilador) cria informações de depuração em tempo de compilação. O depurador usa essas informações para mostrar nomes de variável e outras informações em um formato útil quando você estiver depurando. Se você compilar seu programa sem essas informações, a funcionalidade do depurador será limitada. Para obter mais informações, consulte [/Debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|**Definir constante DEBUG**|Definir esse símbolo permite a compilação condicional das funções de saída a [classe Debug](/dotnet/api/system.diagnostics.debug). Com esse símbolo definido, métodos de classe de depuração geram a saída para o [a janela de saída](../ide/reference/output-window.md). Sem esse símbolo, os métodos da classe de depuração não são compilados e nenhuma saída será gerada. Esse símbolo deve ser definido na versão de depuração e não na versão de lançamento. Definir esse símbolo em uma versão de lançamento cria código desnecessário que deixa a execução do seu programa mais lenta.|  
|**Definir constante TRACE**|Definir esse símbolo permite a compilação condicional das funções de saída a [classe Trace](/dotnet/api/system.diagnostics.trace.aspx). Com esse símbolo definido, os métodos de classe de rastreamento geram a saída para o [a janela de saída](../ide/reference/output-window.md). Sem esse símbolo, os métodos da classe de rastreamento não são compilados e nenhuma saída de rastreamento será gerada. Esse símbolo é definido por padrão para as versões de depuração e lançamento.|  
  
## <a name="see-also"></a>Consulte também  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)