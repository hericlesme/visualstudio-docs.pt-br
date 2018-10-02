---
title: Estado de VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: douge
ms.openlocfilehash: 2891e3f8f9022aad3d16245ae1553a1a9fec3ec7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475968"
---
# <a name="vspackage-state"></a>Estado de VSPackage
Muitos fatores determinam o conjunto de valores persistentes ou o estado de um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aplicativo.  
  
-   Projetos têm propriedades do projeto e configuração.  
  
-   As soluções têm propriedades.  
  
-   Configurações do usuário determinam o tamanho e posição das janelas de documentos, janelas de ferramentas, estado de encaixe e atalhos de teclado.  
  
-   Aplicativos podem ter opções que o usuário define.  
  
-   Objetos que cria um aplicativo podem ter suas próprias propriedades.  
  
 Aqui estão algumas das maneiras que um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o estado do aplicativo pode ser gerenciado:  
  
-   Por meio das páginas de propriedades do projeto e solução.  
  
-   Por meio de **Import and Export Settings Wizard**, que permite que um usuário mover as configurações de um computador para outro.  
  
-   Por meio de **opções** caixa de diálogo que inclui opções relacionadas aos aplicativos.  
  
-   Por meio de **propriedades** janela, que expõe as propriedades de objetos.  
  
-   Por meio da automação. Um aplicativo pode acessar propriedades de VSPackage e objetos que têm sido expostas para a automação.  
  
 O estado do aplicativo de base é vários mecanismos de persistência que permitem que o estado do aplicativo ser salvo e restaurado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Suporte para persistência de estado](../misc/support-for-state-persistence.md)  
 Lista as estratégias comuns para salvar, restaurando e redefinindo o estado de um VSPackage.  
  
 [Opções e páginas de opções](../extensibility/internals/options-and-options-pages.md)  
 Apresenta as páginas de opções gerais e personalizadas e explica como implementá-los.  
  
 [Criar uma página de opções](../extensibility/creating-an-options-page.md)  
 Explica como criar duas páginas de opções, uma página simples e uma página personalizada.  
  
 [Suporte para categorias de configurações](../misc/support-for-settings-categories.md)  
 Discute as configurações de usuário e como elas são criadas e mantidas.  
  
 [Criar uma categoria de configurações](../extensibility/creating-a-settings-category.md)  
 Explica como criar um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] categoria de configurações e usá-lo para salvar os valores e restaurar valores de um arquivo de configurações.  
  
 [Estender propriedades e a janela de propriedades](../extensibility/extending-properties-and-the-property-window.md)  
 Explica como exibir e alterar o valor de um objeto na **propriedades** janela.  
  
 [Expor propriedades à janela de propriedades](../extensibility/exposing-properties-to-the-properties-window.md)  
 Explica como expor as propriedades públicas de um objeto para o **propriedades** janela.  
  
 [Suporte para propriedades de projeto e configuração](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Explica como exibir e alterar as propriedades do projeto e configuração.  
  
 [Obter propriedades do projeto](../extensibility/getting-project-properties.md)  
 Orienta você pelas etapas de criação de um VSPackage gerenciado que exibe as propriedades do projeto em uma janela de ferramenta.  
  
 [Usar o armazenamento de configurações](../extensibility/using-the-settings-store.md)  
 Explica o mecanismo de persistência de Store de configurações e como usá-lo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Fornece uma orientação geral para tópicos que explicam como criar e usar os VSPackages.