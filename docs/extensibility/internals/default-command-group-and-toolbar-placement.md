---
title: "Padrão de comando, o grupo e o posicionamento da barra de ferramentas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 84e850d44162a964ce6ef8b64be92ce4eeacb86e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="default-command-group-and-toolbar-placement"></a>Comando padrão, o grupo e o posicionamento da barra de ferramentas
Para a uniformidade de produto e estabilidade, a interface do usuário exibe determinados grupos de comando por padrão, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece definições para comandos e grupos de comando. VSPackages também pode usar os comandos padrão e os grupos de comando.  
  
 Os grupos de comando padrão se enquadram em três categorias: IDE comandos, os comandos de produto e comandos do editor.  
  
## <a name="default-ide-commands"></a>Comandos do IDE padrão  
 A barra de ferramentas padrão IDE inclui comandos compartilhados por todos os produtos contidos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Isso inclui comandos relacionadas a operações de projeto genérico, como o **salvar** comando e o **Adicionar Item** comando. VSPackages não deve adicionar a ou subtrair nessa barra de ferramentas, com uma exceção: se o produto ou o VSPackage adiciona uma nova janela de ferramenta, a janela deve ser adicionada à lista de janelas de ferramentas disponíveis no **exibição** menu. Novos produtos ou VSPackages pode adicionar suas próprias ferramentas.  
  
## <a name="default-product-commands"></a>Comandos de produto padrão  
 Cada produto pode fornecer o IDE com sua própria barra de ferramentas padrão que contém importantes e comandos usados com frequência. No entanto, é melhor, use menus e barras de ferramentas sempre que possível existentes e complementá-los com outras barras de ferramentas de tarefas específicas, conforme necessário.  
  
 O campo de prioridade de uma barra de ferramentas determina o posicionamento de linha. Zero a prioridade coloca a barra de ferramentas na terceira linha (linha 3), abaixo da barra de menu (linha 1) e o **padrão** barra de ferramentas (linha 2). Portanto, outras barras de ferramentas são exibidos na linha (prioridade + 3). Barras de ferramentas subsequentes são colocadas na mesma linha, se houver espaço; Caso contrário, eles são movidos automaticamente para a próxima linha.  
  
## <a name="default-editor-commands"></a>Comandos de Editor padrão  
 Um VSPackage que fornece um editor personalizado deve fornecer uma barra de ferramentas padrão que contém o mais importante e comandos usados com frequência no editor. A barra de ferramentas do editor deve aparecer quando o editor está ativo e deve ser ocultado quando o editor não está ativo. Essa visibilidade é controlada no `VisibilityConstraints Element` do arquivo. VSCT.  
  
 Barras de ferramentas do Editor devem ser colocadas abaixo barras de ferramentas do IDE e produto.  
  
## <a name="see-also"></a>Consulte também  
 [Grupos, Menus e comandos definidos pelo IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)