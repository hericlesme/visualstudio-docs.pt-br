---
title: "Como gerenciar configurações de build com as configurações do Visual Basic Developer aplicadas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 094f87ca4a56f71cbecfa9b6b1dc9189244c0c57
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Como gerenciar configurações de build com as configurações do Visual Basic Developer aplicadas
Por padrão, todas as opções avançadas de configuração de build ficam ocultas com as configurações do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Developer aplicadas. Este tópico explica como habilitar essas configurações manualmente.  
  
## <a name="enabling-advanced-build-configurations"></a>Habilitando configurações de build avançadas  
 Por padrão, as configurações do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Developer ocultam a opção de abrir a caixa de diálogo do **Configuration Manager** e as listas **Configuração** e **Plataforma** no [Designer de Projeto](..//ide/reference/application-page-project-designer-visual-basic.md).  
  
#### <a name="to-enable-advanced-build-configurations"></a>Para habilitar configurações de build avançadas  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  Expanda **Projetos e Soluções** e clique em **Geral**.  
  
    > [!NOTE]
    >  O nó **Geral** permanece visível mesmo que a opção **Mostrar todas as configurações** seja desmarcada. Se quiser ver todas as opções disponíveis, clique em **Mostrar todas as configurações**.  
  
3.  Clique em **Mostrar configurações avançadas de build**.  
  
4.  Clique em **OK**.  
  
     No menu **Build**, **Configuration Manager** agora está disponível e as listas **Configuração** e **Plataforma** estão visíveis no Designer de Projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Noções sobre configurações de build](../ide/understanding-build-configurations.md)   
 [Compilando e criando](../ide/compiling-and-building-in-visual-studio.md)