---
title: Diretrizes de posicionamento de comando | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5c79d58530a7f6afc5779fab1bc0b5a1626cb595
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="command-placement-guidelines"></a>Diretrizes de posicionamento de comando
Práticas recomendadas para comandos de posicionamento no ambiente de desenvolvimento integrado (IDE) do Visual Studio variam dependendo do tamanho do conjunto de comandos. Comandos são definidos e posicionados de acordo com as informações nos arquivos. VSCT.  
  
## <a name="best-practices-for-all-command-sets"></a>Práticas recomendadas para todos os conjuntos de comandos  
 Para cada conjunto de comandos, siga estas diretrizes:  
  
-   Prepare um gráfico da estrutura de comando com antecedência. Identificar os comandos, caixas de combinação, grupos de comando e menus de atalho que serão usados em mais de um local.  
  
-   Os comandos que aparecem no mesmo grupo devem estar relacionados.  
  
-   Grupos que contêm apenas um comando são aceitáveis.  
  
-   Pacotes não devem adicionar muitos dos comandos a menus existentes do Visual Studio. Em vez disso, eles devem criar menus ou submenus para hospedar novos comandos.  
  
-   Quando você colocar um comando em um menu existente, o nome do comando para que sua finalidade é criptografada e não será ser confundido com comandos existentes.  
  
## <a name="best-practices-for-small-command-sets"></a>Práticas recomendadas para conjuntos de comandos pequeno  
 Se você estiver desenvolvendo um VSPackage que tem apenas alguns comandos, também siga estas diretrizes:  
  
-   Quando possível, use o [elemento pai](../../extensibility/parent-element.md) de um comando, a caixa de combinação, grupo ou o menu filho para colocá-la no grupo apropriado.  
  
-   Atribua grupos a menus exibidos pelo VSPackage.  
  
-   O pai de um menu filho ou um comando deve ser um [elemento Group](../../extensibility/group-element.md). Atribuir comandos e menus filho aos grupos e, em seguida, atribua os grupos de menus do pai.  
  
-   Você pode colocar um comando em grupos adicionais, adicionando um [CommandPlacements elemento](../../extensibility/commandplacements-element.md) seção após a definição do comando e, em seguida, adicionar o `CommandPlacements Element` um [CommandPlacement elemento](../../extensibility/commandplacement-element.md) para cada grupo adicional.  
  
## <a name="best-practices-for-large-command-sets"></a>Práticas recomendadas para conjuntos de comandos grandes  
 Se seu VSPackage terá muitos comandos que serão exibido em vários contextos, também siga estas diretrizes:  
  
-   Verifique os menus, grupos e comandos que o domínio pai. Ou seja, não atribua um `Parent Element` na definição do item.  
  
-   Use `CommandPlacement Element` entradas na `CommandPlacements Element` seção colocar menus, grupos e comandos em seus menus de pai e grupos.  
  
-   No `CommandPlacements` seção, as entradas que preenchem um determinado menu ou grupo deve estar adjacente uns aos outros. Isso ajuda a legibilidade e torna o `Priority` classificações mais fácil de determinar.  
  
## <a name="see-also"></a>Consulte também  
 [Como VSPackages adicionar elementos da Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)