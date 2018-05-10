---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2c678d7304c879cf42c24de9d83704971043676
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no modo de segurança, carregando apenas o ambiente e os serviços padrão.

## <a name="syntax"></a>Sintaxe

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Comentários
 Essa opção impede que todos os VSPackages de terceiros sejam carregados quando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é iniciado, garantindo assim uma execução estável.

## <a name="description"></a>Descrição
 O exemplo a seguir inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no modo de segurança.

## <a name="code"></a>Código

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)