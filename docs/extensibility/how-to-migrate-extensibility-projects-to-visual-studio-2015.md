---
title: 'Como: migrar projetos de extensibilidade para o Visual Studio 2015 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5adad311c1696d958902d9ad33ed1d1872606458
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Como: migrar projetos de extensibilidade para o Visual Studio 2015
Aqui está como atualizar sua extensão.  
  
> [!IMPORTANT]
>  Se você pretende manter uma versão de sua solução de extensão para uma versão anterior do Visual Studio, certifique-se de fazer uma cópia antes de atualizá-lo. Pode ser difícil retornar a versão atualizada para seu estado anterior.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Para atualizar uma solução de extensibilidade  
  
1.  Usando a cópia que você deseja atualizar, abra-a na nova versão. Você será avisado de que a atualização não é reversível.  
  
2.  Após a conclusão da atualização, altere o caminho do programa externo para a nova versão do devenv.exe. Clique com botão direito no nó do projeto no **Solution Explorer**, em seguida, escolha **propriedades**. No **depurar** guia, localize a caixa de texto por **Iniciar programa externo** e altere o caminho do devenv.exe para o caminho do Visual Studio 2015, que deve ter esta aparência:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Adicione uma referência a Microsoft.VisualStudio.Shell.14.0.dll. (Com o botão direito no nó do projeto no **Solution Explorer** e, em seguida, escolha **adicionar /Reference**. Selecione o **extensões** guia e, em seguida, verificar **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Compile a solução. Os arquivos compilados são implantados no:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nome do autor\>\\< nome do projeto\>\\< versão do projeto\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Para atualizar um projeto de extensibilidade para assemblies de referência do SDK do VS NuGet  
  
1.  Determine os assemblies de referência de SDK do VS que precisa de seu projeto.  Em **Solution Explorer**, expanda o projeto **referências** nó e revise a lista de referências do projeto.  Assemblies do SDK do VS referências terão o prefixo **Microsoft.VisualStudio** o nome (por exemplo: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Remove os assemblies de referência do SDK do VS do projeto, selecionando-os, clique com botão direito e **remover**.  
  
3.  Adicione as versões do NuGet dos assemblies de referência do SDK do VS.  Enquanto estiver no **Solution Explorer referências** nó, abra o **gerenciar pacotes NuGet...**  caixa de diálogo.  Se você quiser saber mais sobre essa caixa de diálogo, consulte [Package Manager UI](/NuGet/Tools/Package-Manager-UI). Os assemblies de referência do SDK do VS são publicados em [nuget.org](http://www.nuget.org) por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Usando **nuget.org** como seu **origem do pacote**, procure o nome do pacote NuGet que corresponda ao assembly de referência desejada (por exemplo: Microsoft.VisualStudio.Shell.14.0) e instalá-lo no seu projeto.  O NuGet pode adicionar vários assemblies de referência para satisfazer as dependências do assembly inicial.  
  
     Se preferir, você pode adicionar todos os assemblies de referência de SDK do VS uma vez por instalação do SDK do VS [pacote Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Você também pode alternar para usar a versão do NuGet das ferramentas de compilação do SDK do VS. Este pacote do NuGet é [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) e uma vez adicionado ao seu projeto será incluem as ferramentas necessárias e arquivos para permitir que você compilar o projeto de extensibilidade em um computador sem o SDK do VS instalado de destino.  
  
> [!NOTE]
>  Não é necessário que você atualize seus projetos de extensibilidade existentes para usar assemblies de referência do NuGet e ferramentas.  Eles podem continuar a criar usando assemblies de referência e as ferramentas instaladas com o SDK do VS.