---
title: Hierarquias no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d1f018b9cc48d059761a26721c808024f60bb3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129916"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarquias no Visual Studio
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) exibe um projeto como uma *hierarquia*. No IDE, uma hierarquia é uma árvore de nós, onde cada nó tem um conjunto de propriedades associadas. Um *projeto hierarquia* é um contêiner que mantém os itens do projeto, relações dos itens e propriedades associadas a itens e comandos.  
  
 Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], gerenciar hierarquias de projeto usando a interface de hierarquia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface redireciona comandos invocar a partir de itens de projeto para a janela de hierarquia apropriada em vez do manipulador de comando padrão.  
  
## <a name="project-hierarchies"></a>Hierarquias de projeto  
 Cada hierarquia de projeto contém itens que você pode exibir e editar. Esses itens variam dependendo do tipo de projeto. Por exemplo, um projeto de banco de dados pode conter procedimentos armazenados, exibições de banco de dados e tabelas de banco de dados. Um projeto de linguagem de programação, por outro lado, provavelmente incluirá arquivos de origem e arquivos de recursos para bitmaps e caixas de diálogo. Hierarquias podem ser aninhadas, que oferece algumas maior flexibilidade quando você criar uma hierarquia de projeto.  
  
 Quando você cria um novo tipo de projeto, o tipo de projeto controla o conjunto completo de itens que podem ser editadas nele. No entanto, os projetos podem conter itens para os quais não têm suporte de edição. Por exemplo, os projetos do Visual C++ podem conter arquivos HTML, mesmo que o Visual C++ não fornece qualquer editor personalizado para o tipo de arquivo HTML.  
  
 Hierarquias de gerenciam a persistência de itens que eles contêm. A implementação da hierarquia deve controlar propriedades especiais que afetam a persistência dos itens dentro da hierarquia. Por exemplo, se os itens representam objetos em um repositório em vez de arquivos, a implementação de hierarquia deve controlar a persistência dos objetos. O IDE em si direciona a hierarquia para salvar os itens em conformidade com a entrada do usuário, mas o IDE não controla as ações necessárias para salvar esses itens. Em vez disso, o projeto está no controle.  
  
 Quando um usuário abre um item em um editor, a hierarquia que controla esse item é selecionada e torna-se a hierarquia ativa. A hierarquia selecionada determina o conjunto de comandos disponíveis para agir sobre o item. Controle o foco do usuário dessa maneira permite que a hierarquia refletir o contexto do usuário atual.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de projeto](../../extensibility/internals/project-types.md)   
 [A seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Exemplos de VSSDK](http://aka.ms/vs2015sdksamples)