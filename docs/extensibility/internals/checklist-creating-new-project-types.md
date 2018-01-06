---
title: "Lista de verificação: Criar novos tipos de projeto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ea9c2ebd295fe463192c50da402240e0b1df1304
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="checklist-creating-new-project-types"></a>Lista de verificação: Criar novos tipos de projeto
Você deve concluir várias tarefas para criar um novo tipo de projeto. A lista de verificação a seguir fornece um guia para essas tarefas.  
  
1.  Crie a funcionalidade para o novo tipo de projeto. Para obter mais informações, consulte [decisões de Design de tipo de projeto](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Determine quais editores são usados para o código e outros elementos de projeto. Você pode usar o principal ou editores padrão, ou você pode criar e usar os editores específicos do projeto. Para obter mais informações, consulte [criação personalizada editores e Designers](../../extensibility/creating-custom-editors-and-designers.md) e [como: editores específicos de projeto abertos](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Determinar o nível de participação terão seus itens de projeto no **exibição de classe** e **Pesquisador de objetos**. Para obter mais informações, consulte [ferramentas de navegação de símbolo de suporte](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Derive novas classes com base nas decisões de design que você fez anteriormente para seu projeto e itens de projeto.  
  
5.  Escreva o código para os seguintes componentes do tipo de projeto:  
  
    -   Fábrica de projeto, para gerenciar a criação de novos projetos e abrir projetos existentes. Para obter mais informações, consulte [criar projeto instâncias por usando fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Hierarquia de projeto e manipulação de comandos. Para obter mais informações, consulte [não está em compilação: usando Classes de projeto HierUtil7 para implementar um tipo de projeto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md), [componentes principais do modelo de projeto](../../extensibility/internals/project-model-core-components.md)e [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Gerenciamento de itens de projeto, incluindo a adição de seu projeto para o **novo projeto** caixa de diálogo. Para obter mais informações, consulte [adicionando projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md) e [registro de modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistência de estado do projeto e itens individuais. Para obter mais informações, consulte [abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md). Para a persistência de informações de solução, consulte [soluções](../../extensibility/internals/solutions.md).  
  
    -   Propriedades independentes de configuração para exibir na janela Propriedades. Para obter mais informações, consulte [estendendo propriedades](../../extensibility/internals/extending-properties.md).  
  
    -   Propriedades de configuração do projeto conforme implementado nas páginas de propriedades para mostrar as propriedades de configuração dependente. Para obter mais informações, consulte [gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Enumerando saídas para a implantação. Para obter mais informações, consulte [configuração do projeto para a saída](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Serviços de inicialização do projeto. Para obter mais informações, consulte [elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md) e [componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objetos ou classes derivadas de `IDispatch`, disponível para automação.  
  
    -   Arquivos de tabela de comando XML (. VSCT). Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testar, depurar e iniciar o tipo de projeto.  
  
7.  Exibir seu projeto no **projeto** guia do **adicionar referência** caixa de diálogo definindo `VARIANT_TRUE` como o valor para `VSHPROPID_ShowProjInSolutionPage`. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Crie o arquivo do Microsoft Installer (. msi) para instalar os VSPackages. Para obter mais informações, consulte [instalando VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registro de um tipo de projeto](../../extensibility/internals/registering-a-project-type.md), e [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Consulte também  
 [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quando criar tipos de projeto](../../extensibility/internals/when-to-create-project-types.md)   
 [Criar tipos de projeto](../../extensibility/internals/creating-project-types.md)