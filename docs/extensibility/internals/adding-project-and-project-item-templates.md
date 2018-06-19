---
title: Adicionando o projeto e modelos de Item de projeto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94d521d288b470db56736668f11d47dab71d2533
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128740"
---
# <a name="adding-project-and-project-item-templates"></a>Adicionando o projeto e modelos de Item de projeto
Quando você cria seus próprios tipos de projeto, você deve fornecer suporte para a adição de novos projetos e itens de projeto usando o padrão [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrado caixas de diálogo (IDE) do ambiente de desenvolvimento. Os tópicos a seguir discutem as técnicas diferentes para adicionar projetos e itens de projeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Contexto do projeto](../../extensibility/internals/project-context.md)  
 Explica que o projeto fornece a maioria das informações de contexto para o que ocorre no ambiente.  
  
 [Prioridade do projeto](../../extensibility/internals/project-priority.md)  
 Explica o que um item de projeto geralmente é um membro de um projeto para ajudar a evitar a ambiguidade sobre o qual o projeto é usado para abrir o item.  
  
 [Projeto de arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md)  
 Fornece informações sobre os dois tipos de editores que podem ser usados para abrir arquivos em um projeto e a função que o projeto desempenha determinar qual editor a ser usado quando um item de projeto é aberto.  
  
 [Registrar modelos de projeto e de item](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explica o que ocorre quando um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto é criado.  
  
 [Adicionar itens às caixas de diálogo Adicionar Novo Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explica o processo de adição de itens para o **Adicionar Novo Item** caixa de diálogo.  
  
 [Adicionar diretórios à caixa de diálogo Novo Projeto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Fornece um exemplo de como registrar um novo diretório que contém os modelos personalizados disponibilizados por um VSPackage.  
  
 [Adicionar diretórios à caixa de diálogo Adicionar Novo Item](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Fornece um exemplo de como registrar um novo conjunto de diretórios para o **Adicionar Novo Item** caixa de diálogo.  
  
 [Comandos definidos pelo IDE para estender sistemas de projeto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Lista os tipos diferentes de itens de comando usados para estender a sistemas de projeto.  
  
 [CATIDs para objetos normalmente usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Lista as CATIDs para objetos que são usados para estender [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemas de projeto.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Como abrir editores específicos a um projeto](../../extensibility/how-to-open-project-specific-editors.md)  
 Fornece instruções passo a passo para abrir um item intrinsecamente associado a um editor específico para um projeto.  
  
 [Como abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)  
 Fornece instruções passo a passo para abrir um editor padrão.  
  
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)  
 Fornece links para tópicos conceituais sobre o subtipo de projeto. Subtipos de projeto estendem existente [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projetos.  
  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Fornece links para tópicos adicionais que oferecem informações sobre como criar novos tipos de projeto.