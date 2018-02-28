---
title: Como adicionar um arquivo app.config a um projeto no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: d77e86599670ef04b813381da84a03ab1f238af3
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Como adicionar um Arquivo de Configuração do Aplicativo a um projeto C#

Ao adicionar um arquivo de configuração de aplicativo (arquivo app.config) a um projeto C#, você pode personalizar o modo como o Common Language Runtime localiza e carrega arquivos do assembly. Para saber mais sobre arquivos de configuração de aplicativo, veja [Como o tempo de execução localiza assemblies (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Os aplicativos UWP não contêm um arquivo app.config.

Quando você compila seu projeto, o ambiente de desenvolvimento copia automaticamente o arquivo app.config, altera o nome do arquivo da cópia para corresponder ao executável e, em seguida, move a cópia para o diretório **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Para adicionar um arquivo de configuração de aplicativo a um projeto C#

1. Na barra de menus, escolha **Projeto** > **Adicionar Novo Item**.

     A caixa de diálogo **Adicionar Novo Item** é exibida.

1. Expanda **Instalado** > **Itens do Visual C#** e, em seguida, escolha o modelo **Arquivo de Configuração de Aplicativo**.

3.Na caixa e texto **Nome**, insira um nome e escolha o botão **Adicionar**.

     A file named app.config is added to your project.

## <a name="see-also"></a>Consulte também

[Gerenciando configurações de aplicativo (.NET)](../ide/managing-application-settings-dotnet.md)  
[Esquema do arquivo de configuração (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)  
[Configuração de aplicativos (.NET Framework)](/dotnet/framework/configure-apps/index)