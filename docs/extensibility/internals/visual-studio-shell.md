---
title: Shell do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63b8420b3941114f8edd1e494c8469ae4b81ba79
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-shell"></a>Shell do Visual Studio
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell é o principal agente de integração em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. O shell fornece a funcionalidade necessária para habilitar VSPackages compartilhar serviços comuns. Como a meta de arquitetura de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é casaco principal funcionalidade em VSPackages, o shell é uma estrutura para fornecer a funcionalidade básica e dar suporte a comunicação cruzada entre seu componente VSPackages.  
  
## <a name="shell-responsibilities"></a>Responsabilidades do shell  
 O shell tem as seguintes responsabilidades de chave:  
  
-   Elementos básicos de suporte (por meio de interfaces COM) da interface do usuário (IU). Esses incluem menus padrão e barras de ferramentas, quadros de janela de documento ou janelas filho de interface de documentos múltiplos (MDI), os quadros de janela de ferramenta e suporte de encaixe.  
  
-   Manter uma lista de execução de todos os documentos abertos em uma tabela de documento (RDT) em execução para coordenar a persistência de documentos e a garantia de que um documento não pode ser aberto em mais de uma forma ou formas incompatível.  
  
-   Suporte a interface de roteamento de comando e manipulação de comandos, `IOleCommandTarget`.  
  
-   Carregando VSPackages em momentos apropriados. Um VSPackage de carregamento de atraso é necessário para melhorar o desempenho do shell.  
  
-   Gerenciando determinados serviços compartilhados, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, que fornece a funcionalidade básica do shell, e <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que fornece a funcionalidade básica de janelas.  
  
-   Gerenciando os arquivos de solução (. sln). As soluções contêm grupos de projetos relacionados, semelhantes aos arquivos de espaço de trabalho (dsw) no Visual C++ 6.0.  
  
-   Seleção de todo o shell do controle de contexto e moeda. O shell rastreia os seguintes tipos de itens:  
  
    -   O projeto atual  
  
    -   O item de projeto atual ou ItemID atual<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   A seleção atual para o **propriedades** janela ou`SelectionContainer`  
  
    -   O contexto de interface do usuário IDs ou CmdUIGuids que controlam a visibilidade de comandos, menus e barras de ferramentas  
  
    -   Os elementos ativos no momento, como a janela ativa, o documento e o Gerenciador de desfazer  
  
    -   Os atributos de contexto de usuário que orientam ajuda dinâmica  
  
 O shell também atua como mediador comunicação entre VSPackages instalados e os serviços atuais. Ele dá suporte a recursos principais do shell e torna disponível para todos os VSPackages integrados no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Esses recursos principais incluem os seguintes itens:  
  
-   **Sobre** tela inicial e de caixa de diálogo  
  
-   **Adicionar novo e Adicionar Item existente** caixas de diálogo  
  
-   **Exibição de classe** janela e **Pesquisador de objetos**  
  
-   **Referências** caixa de diálogo  
  
-   **Estrutura de tópicos de documento** janela  
  
-   **Ajuda dinâmica** janela  
  
-   **Localizar** e **substituir**  
  
-   **Abra o projeto** e **abrir arquivo** em caixas de diálogo o **novo** menu  
  
-   **Opções de** caixa de diálogo de **ferramentas** menu  
  
-   **Propriedades** janela  
  
-   **Gerenciador de Soluções**  
  
-   **Lista de tarefas** janela  
  
-   **Caixa de Ferramentas**  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackages](../../extensibility/internals/vspackages.md)