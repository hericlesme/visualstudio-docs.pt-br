---
title: Criar tipos de projeto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7c0bba9b80e4e874f222ce00834f44a2d93e3e7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-project-types"></a>Criar tipos de projeto
Você pode estender [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] criando um novo tipo de projeto. Para criar um novo tipo de projeto, você deve compreender vários conceitos e concluir várias etapas. Os tópicos a seguir fornecem uma visão geral de como criar tipos de projeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Decisões de design do tipo de projeto](../../extensibility/internals/project-type-design-decisions.md)  
 Descreve o item, persistência de arquivo de projeto e compromisso mechanic decisões de design que você precisa fazer antes de criar um novo tipo de projeto.  
  
 [Lista de verificação: criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Fornece uma visão geral das etapas que você deve seguir para criar um novo tipo de projeto que oferece suporte a tarefas de programação como edição de código e compilação, compilar, depurar e implantar aplicativos em seu projeto.  
  
 [Criar instâncias de projetos usando fábricas de projetos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Fornece informações sobre como fornecer e usar uma fábrica de projeto para criar instâncias de um novo projeto.  
  
 [Registrar um tipo de projeto](../../extensibility/internals/registering-a-project-type.md)  
 Fornece exemplos de código de instruções do registro que fornecem os caminhos padrão e dados e uma tabela que contém entradas do script do registro para cada instrução.  
  
 [Persistência do projeto](../../extensibility/internals/project-persistence.md)  
 Discute o uso de `IPersistFileFormat` para manter os arquivos e objetos do projeto não é baseado em arquivo.  
  
 [Usar o MSBuild](../../extensibility/internals/using-msbuild.md)  
 Descreve como o tipo de projeto pode usar o [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] build engine para permitir que os usuários de compilação de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e na linha de comando.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Suporte a ferramentas de navegação por símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explica a arquitetura de código, como ferramentas de visualização de **Pesquisador de objetos** e **exibição de classe** janela. Descreve as interfaces e métodos que são usados para implementar a pesquisa de objetos em um VSPackage.  
  
 [Adicionar modelos projeto e de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Discute a importância que projetos representam determinar qual editor é usado quando um item de projeto é aberto e como os recursos de projeto podem ser manipulados.  
  
 [Instalar VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Mostra como fornecer o VSPackage sua própria identidade exclusiva e como encapsular seu VSPackage DLLs e outras informações em um pacote do Windows Installer (. Arquivo MSI) para implantação para seus clientes.  
  
 [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Descreve como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hierarquias de modos de exibição e endereços.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Fornece uma visão geral de um VSPackage, um objeto COM instalável que estende o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente e discute como implementar seu próprio VSPackage.  
  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Discute como usar projetos para modificar o código, compilação e compilar o código e executar e depurar o código e fornece links para tópicos detalhados sobre como criar tipos de projeto.