---
title: Definido pelo IDE comandos, Menus e grupos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b65266ad3367df5cebeabc251bc8bceb6cda7075
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ide-defined-commands-menus-and-groups"></a>Grupos, Menus e comandos definidos pelo IDE
Muitos menus, comandos e grupos de comando já estão definidos para uso pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Esses comandos também estão disponíveis para uso quando você estende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Localizando definido pelo ambiente de comandos  
 Os comandos de ambiente são definidos em um conjunto de quatro arquivos. VSCT:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Esses arquivos estão localizados em  *\<caminho de instalação do SDK do Visual Studio >*\VisualStudioIntegration\Common\Inc\\. Esses arquivos fornecem as definições e os GUIDs dos menus e grupos que você pode usar no arquivo de configuração (. VSCT) de tabela de comandos do seu VSPackage como contêineres para seus próprios menus, grupos e comandos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [GUIDs e IDs de menus do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Fornece os valores GUID e ID de menus na barra de menus do Visual Studio e dos grupos de que eles contêm.  
  
 [GUIDs e IDs de barras de ferramentas do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Fornece os valores GUID e ID de barras de ferramentas no IDE do Visual Studio e os grupos que elas contêm.  
  
 [GUIDs e IDs de comandos do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Fornece os valores GUID e ID de comandos definidos pelo Visual Studio IDE.  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comandos definidos pelo IDE para a extensão de sistemas de projeto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)