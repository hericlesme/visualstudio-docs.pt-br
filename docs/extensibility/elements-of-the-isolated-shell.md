---
redirect_url: shell/elements-of-the-isolated-shell
title: Elementos do Shell isolado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15c32ccd3634529c63eb95eb698c3239b6c0e37e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="elements-of-the-isolated-shell"></a>Elementos do Shell isolado
Você pode modificar as configurações do registro, configurações de tempo de execução e ponto de entrada do aplicativo de seu aplicativo de shell isolado e. VSCT, .pkgdef, and.pkgundef arquivos.  
  
## <a name="registry-settings"></a>Configurações do registro  
 Os arquivos .pkgundef e o .pkgdef modificar as configurações do registro para o aplicativo de shell isolado. Quando o aplicativo é executado, as configurações do registro são definidas na sequência a seguir:  
  
 Quando o aplicativo é executado, as configurações do registro são definidas na sequência a seguir:  
  
1.  A chave do registro para o aplicativo é criada.  
  
2.  O registro é atualizado do arquivo do aplicativo .pkgdef definindo entradas e chaves especificadas.  
  
3.  Para cada pacote que faz parte do seu aplicativo, o registro é atualizado do arquivo .pkgdef do pacote. Cada pacote é definido no arquivo .pkgdef do aplicativo, o $RootKey$ \Packages\\{*vsPackageGuid*} chave para o pacote.  
  
4.  O registro é atualizado a partir de AppEnvConfig.pkgdef e BaseConfig.pkgdef no *caminho de instalação do SDK do Visual Studio*\Common7\IDE\ShellExtensions\Platform directory. Esses arquivos são parte do Visual Studio e também a parte do pacote redistribuível do Visual Studio Shell (modo isolado).  
  
5.  O registro é atualizado do arquivo do aplicativo .pkgundef removendo entradas e chaves especificadas.  
  
## <a name="run-time-settings"></a>Configurações de tempo de execução  
 Quando um usuário inicia o aplicativo de shell isolado, ele chama o ponto de entrada inicial do shell do Visual Studio. Configurações do aplicativo são definidas quando o aplicativo é iniciado, da seguinte maneira:  
  
1.  Shell do Visual Studio verifica o registro do aplicativo para as chaves específicas. Se a configuração de uma chave for especificada na chamada para o ponto de entrada de início, esse valor substitui o valor do registro.  
  
2.  Se o ponto de registro nem a entrada de parâmetro especifica o valor de uma configuração, é usado o valor padrão para a configuração.  
  
 Quando um usuário inicia o aplicativo de linha de comando, todas as opções de linha de comando são passadas para o shell do Visual Studio, que trata da mesma maneira que faz Devenv. Para obter mais informações sobre opções de Devenv, consulte [opções de linha de comando Devenv](../ide/reference/devenv-command-line-switches.md) e [Devenv opções de linha de comando para o desenvolvimento de VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Para obter mais informações sobre como um pacote registra para opções de linha de comando, consulte [Adicionando opções de linha de comando](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>O ponto de entrada inicial  
 O arquivo Appenvstub.dll contém pontos de entrada para acessar o shell isolado. Quando o aplicativo for iniciado, ele chama o ponto de entrada de início de Appenvstub.dll.  
  
 Você pode alterar o comportamento do aplicativo, alterando o valor do último parâmetro que é passado para o ponto de entrada inicial. Para obter mais informações, consulte [isolado Shell entrada ponto parâmetros (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>A. Arquivo VSCT  
 O arquivo. VSCT permite que você especifique quais elementos de interface de usuário do Visual Studio padrão estão disponíveis no aplicativo. Para obter mais informações, consulte [. Arquivos de VSCT](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>A. Arquivo Pkgundef  
 Quando o aplicativo é instalado em um computador em que o Visual Studio já está instalado, é feita uma cópia das entradas do registro do Visual Studio para o aplicativo. Por padrão, o aplicativo usa VSPackages que já estão instalados no computador. O arquivo .pkgundef permite que você exclua as entradas do registro para remover os elementos específicos do shell do Visual Studio ou extensões do aplicativo. Para obter mais informações, consulte [. Arquivos de Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 O arquivo .pkgundef permite que você exclua as entradas do registro para remover os elementos específicos do shell do Visual Studio ou extensões do aplicativo. Para obter mais informações, consulte [. Arquivos de Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 O conjunto de GUIDs que você pode excluir do pacote estão listados na [pacote GUIDs de recursos do Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>A. Arquivo Pkgdef  
 O arquivo .pkgdef permite definir entradas do registro para o aplicativo que são definidas quando o aplicativo está instalado. Para obter uma descrição do arquivo .pkgdef e uma lista de entradas do registro que usa o shell do Visual Studio, consulte [. Arquivos de Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Cadeias de caracteres de substituição  
 As cadeias de caracteres de substituição usadas nos arquivos .pkgdef e .pkgundef são listadas na [substituição de cadeias de caracteres usadas no. Pkgdef e. Arquivos de Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Outras configurações  
 Se seu aplicativo de shell isolado depende Microsoft.VisualStudio.GraphModel.dll, você precisa adicionar o redirecionamento de associação a seguir ao arquivo. config do seu aplicativo de Shell isolado:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```