---
title: Solucionar problemas de descoberta do modelo no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 72663d56844fcc34164e9408ab14c8ead234683e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="troubleshooting-template-installation"></a>Solucionando problemas de instalação do modelo

Se você tiver problemas de implantação de modelos de projeto ou item, você pode habilitar o log de diagnóstico.

1. Crie um arquivo pkgdef na pasta Common7\IDE\CommonExtensions para a instalação (por exemplo, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) com o seguinte conteúdo:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Abra um Prompt de comando "desenvolvedor" para a instalação por meio de pesquisa na pesquisa do Windows e execute `devenv /updateConfiguration`.

1. Inicie o Visual Studio e iniciar as caixas de diálogo Novo projeto e o novo Item para inicializar as duas árvores do modelo. O log do modelo agora aparece no **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corresponde à ID de instalação da instância do Visual Studio). A inicialização de cada árvore modelo acrescenta as entradas nesse log.

O arquivo de log contém as seguintes colunas:

- **FullPathToTemplate**, que tem os seguintes valores:

    - 1 para implantação baseada em manifesto

    - 0 para implantação baseada em disco

- **TemplateFileName**

- Outras propriedades de modelo

> [!NOTE]
> Para desabilitar o log, remova o arquivo pkgdef ou alterar o valor de `EnableTemplateDiscoveryLog` para `dword:00000000`e, em seguida, execute `devenv /updateConfiguration` novamente.

## <a name="see-also"></a>Consulte também

[Criando modelos personalizados de projeto e item](creating-custom-project-and-item-templates.md)