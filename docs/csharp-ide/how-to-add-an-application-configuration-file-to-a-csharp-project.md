---
title: "Como: adicionar um arquivo de configuração de aplicativo a um projeto c# | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 097e7a2eac78fe85b2a3ab62d5cdf1fd18908d56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Como adicionar um Arquivo de Configuração do Aplicativo a um projeto C#
Adicionando um arquivo de configuração de aplicativo (arquivo App. config) para um projeto c#, você pode personalizar como o common language runtime localiza e carrega arquivos de assembly. Para obter mais informações sobre arquivos de configuração do aplicativo, consulte [como o tempo de execução Localiza Assemblies](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
> [!NOTE]
>  Aplicativos UWP não contém um modelo de App. config.
  
 Quando você compila seu projeto, o ambiente de desenvolvimento copia automaticamente o arquivo App. config, altera o nome de arquivo da cópia para corresponder o executável e, em seguida, move a cópia para o diretório bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Para adicionar um arquivo de configuração do aplicativo ao projeto C#  
  
1.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
2.  Expanda **instalado**, expanda **itens do Visual C#**e, em seguida, escolha o **arquivo de configuração de aplicativo** modelo.  
  
3.  No **nome** caixa de texto, digite um nome e, em seguida, escolha o **adicionar** botão.  
  
     Um arquivo chamado App. config é adicionado ao seu projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando configurações de aplicativo (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Esquema de arquivo de configuração](/dotnet/framework/configure-apps/file-schema/index)   
 [Configuração de aplicativos](/dotnet/framework/configure-apps/index)   
 [Como: configurar um aplicativo para uma versão do .NET Framework de destino](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Usando o Ambiente de Desenvolvimento do Visual Studio para C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)