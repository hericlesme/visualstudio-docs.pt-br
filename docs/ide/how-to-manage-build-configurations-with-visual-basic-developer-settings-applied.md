---
title: Como gerenciar configurações de build com configurações de desenvolvedor do Visual Basic aplicadas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 987419e62d54b44a21a70f625e2a240bd7aecc21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946254"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Como gerenciar configurações de build com configurações de desenvolvedor do Visual Basic aplicadas

Por padrão, todas as opções avançadas de configuração de build ficam ocultas com as configurações do desenvolvedor aplicadas. Este tópico explica como habilitar essas configurações manualmente.

## <a name="enable-advanced-build-configurations"></a>Habilitar configurações de build avançadas

Por padrão, as configurações de desenvolvedor do Visual Basic ocultam a opção de abrir a caixa de diálogo **Configuration Manager** e as listas **Configuração** e **Plataforma** no [Designer de Projeto](..//ide/reference/application-page-project-designer-visual-basic.md).

1.  No menu **Ferramentas**, clique em **Opções**.

2.  Expanda **Projetos e Soluções** e clique em **Geral**.

    > [!NOTE]
    > O nó **Geral** permanece visível mesmo que a opção **Mostrar todas as configurações** seja desmarcada. Se quiser ver todas as opções disponíveis, clique em **Mostrar todas as configurações**.

3.  Clique em **Mostrar configurações avançadas de build**.

4.  Clique em **OK**.

     No menu **Build**, **Configuration Manager** agora está disponível e as listas **Configuração** e **Plataforma** estão visíveis no **Designer de Projeto**.

## <a name="see-also"></a>Consulte também

- [Compreender configurações de build](../ide/understanding-build-configurations.md)
- [Compilar e criar](../ide/compiling-and-building-in-visual-studio.md)