---
title: Configurações do projeto para configurações de depuração c# | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 65b30c1dc0b4306c7104b4d0b3dcd38a2cc55b1d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="project-settings-for--c-debug-configurations"></a>Definições do projeto para configurações de depuração do C#
Você pode alterar as configurações de projeto para uma configuração de depuração c# no **páginas de propriedade** janela, conforme discutido em [configurações Debug e Release](../debugger/how-to-set-debug-and-release-configurations.md). As tabelas a seguir mostram onde localizar configurações relacionadas a depuração no **páginas de propriedade** janela.  
  
> [!WARNING]
>  Este tópico não se aplica a aplicativos UWP. Consulte [iniciar uma sessão de depuração (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Guia de depuração  
  
|**Configuração**|**Descrição**|  
|-----------------|---------------------|  
|**Configuração**|Define o modo para compilar o aplicativo. Escolha entre **ativa (depuração)**, **depurar**, **versão**, **todas as configurações de**.|  
|**Iniciar ação**|Esse grupo de controles especifica a ação que ocorrerá quando você escolhe Iniciar do menu Depurar.<br /><br /> -   **Iniciar projeto** é o padrão e inicia o projeto de inicialização para depuração. Para obter mais informações, consulte [escolhendo o projeto de inicialização](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Iniciar programa externo** permite que você inicie e anexe a um programa que não faz parte de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto. Para obter mais informações, consulte [anexar a um programa em execução](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Iniciar navegador na URL** permite depurar um aplicativo da Web.|  
|**Argumentos de linha de comando**|Especifica argumentos de linha de comando para o programa ser depurado. O nome do comando é o nome do programa especificado em Iniciar programa externo. Se Iniciar Ação for definida para iniciar URL, os argumentos de linha de comando não podem ser especificados.|  
|**Diretório de trabalho**|Especifica o diretório de trabalho do programa que está sendo depurado. No [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], o diretório de trabalho é o diretório a partir do qual o aplicativo é iniciado de \bin\debug por padrão.|  
|**Usar computador remoto**|O nome de um computador remoto onde o aplicativo será executado para fins de depuração ou um [nome do servidor Msvsmon](../debugger/remote-debugging.md). O local do EXE no computador remoto é especificado pela propriedade Caminho da Saída na pasta Propriedades de Configuração, categoria Compilação. O local deve ser um diretório compartilhável no computador remoto.|
|**Habilitar depuração de código não gerenciado**|Permite depurar chamadas para código Win32 nativo (não gerenciado) a partir do seu aplicativo gerenciado.|  
|**Habilitar depuração do SQL Server**|Permite depuração de objetos de banco de dados do SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Guia Build  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|**Símbolos de compilação condicional:**|As constantes DEBUG e TRACE são definidas aqui.<br /><br /> Essas constantes ativam a compilação condicional do [classe Debug](/dotnet/api/system.diagnostics.debug) e [classe Trace](/dotnet/api/system.diagnostics.trace). Com essas constantes definidas, depurar e métodos de classe de rastreamento geram a saída para o [a janela de saída](../ide/reference/output-window.md). Sem essas constantes, os métodos da classe Debug e Trace não são compilados e nenhuma saída será gerada.<br /><br /> -Debug normalmente é definida na versão de depuração de um programa e indefinida na versão de lançamento.<br />-Trace normalmente é definido em versões de depuração e liberação.|  
|**Otimizar código**|A menos que você encontre um bug que apareça somente no código otimizado, deverá deixar essa configuração desativada na versão de Depuração. O código otimizado é mais difícil de depurar porque as instruções não correspondem diretamente a instruções em suas janelas de origem.|  
|**Caminho de saída:**|Normalmente definido para bin\Debug para depuração.|

> [!NOTE]
> Para obter mais informações sobre opções de depuração você encontrar o **avançado** botão, consulte [caixa de diálogo Configurações avançadas de compilação (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). O formato portátil para arquivos de símbolo (. PDB) é o formato de plataforma cruzada mais recente para o .NET Core. 
  
## <a name="see-also"></a>Consulte também  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)