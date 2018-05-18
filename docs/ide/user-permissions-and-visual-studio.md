---
title: Permissões de usuário e o Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08b12e09348a28276d0c5d2f375b26e75c1ac3c5
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="user-permissions-and-visual-studio"></a>Permissões de usuário e o Visual Studio

Por motivos de segurança, você deve executar o Visual Studio como um usuário normal sempre que possível.

> [!WARNING]
> Você deve se certificar de não compilar, iniciar ou depurar qualquer solução do Visual Studio que não venha de uma pessoa de confiança ou de uma localidade confiável.

Você pode fazer quase tudo no IDE do Visual Studio como um usuário normal, mas precisa de permissões de administrador para concluir as seguintes tarefas:

|Área|Tarefa|Para obter mais informações|
|----------|----------|--------------------------|
|Instalação|Instale o Visual Studio.|[Instalar o Visual Studio](../install/install-visual-studio.md)|
||Instalar, atualizar ou remover conteúdo da Ajuda local.|[Instalar e gerenciar o conteúdo local](../ide/install-and-manage-local-content.md)|
|Tipos de aplicativo|Desenvolver soluções do SharePoint.|[Requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)|  
||Adquirir uma licença de desenvolvedor da [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Obter uma licença de desenvolvedor](http://go.microsoft.com/fwlink/?LinkID=241313)|
|Caixa de Ferramentas|Adicionar controles COM clássicos à **Caixa de Ferramentas**.|[Caixa de Ferramentas](../ide/reference/toolbox.md)|
|Suplementos|Instalar e usar suplementos escritos usando COM clássico no IDE.|[Crie suplementos e assistentes](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Compilação|Usar eventos pós-compilação que registram um componente.|[Noções básicas sobre etapas e eventos de build personalizados](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||Incluir uma etapa de registro ao criar projetos do C++.|[Noções básicas sobre etapas e eventos de build personalizados](/cpp/ide/understanding-custom-build-steps-and-build-events)|
|Depuração|Depurar aplicativos que são executados com permissões elevadas.|[Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)|
||Depurar aplicativos que são executados em uma conta de usuário diferente, como sites do ASP.NET.|[Depurar aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Depurar na zona de aplicativos de navegador XAML (XBAP).|[Host do WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Usar o emulador para depurar projetos de serviço de nuvem do Microsoft Azure.|[Depurar um serviço de nuvem no Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|
||Configurar um firewall para depuração remota.|[Depuração remota](../debugger/remote-debugging.md)|
|Ferramentas de desempenho|Criar perfil de um aplicativo.|[Guia do iniciante à criação de perfil de desempenho](../profiling/beginners-guide-to-performance-profiling.md)|
|Implantação|Implantar um aplicativo Web para o IIS (Serviços de Informações da Internet) em um computador local.|[Implantar um aplicativo Web ASP.NET em um provedor de hospedagem usando o Visual Studio ou o Visual Web Developer: Implantar no IIS como um ambiente de teste](http://go.microsoft.com/fwlink/?LinkId=266478)|
>>>>>>> 346075117af3d2bd1fddd9c3aca24516a39fa6a3

## <a name="run-visual-studio-as-an-administrator"></a>Executar o Visual Studio como administrador

Você pode iniciar o Visual Studio com permissões administrativas toda vez que iniciar o IDE ou pode modificar o atalho do aplicativo para sempre ser executado com permissões administrativas. Para obter mais informações, consulte a Ajuda do Windows.

### <a name="run-visual-studio-with-administrative-permissions"></a>Executar o Visual Studio com permissões administrativas

Estas instruções referem-se ao Windows 10. Elas são semelhantes para outras versões do Windows.

1. Abra o menu **Iniciar** e role até o Visual Studio 2017.

1. No menu de contexto ou clicando com o botão direito do **Visual Studio 2017**, selecione **Mais** > **Executar como administrador**.

     Quando o Visual Studio for iniciado, **(Administrador)** será exibido após o nome do produto na barra de título.

## <a name="see-also"></a>Consulte também

- [Portar, migrar e atualizar projetos do Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Instalar o Visual Studio](../install/install-visual-studio.md)