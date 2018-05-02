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
ms.openlocfilehash: eaf137b699b7a02a0ee79099e937767262fce4e9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no modo de segurança, carregando apenas o ambiente e os serviços padrão.

## <a name="syntax"></a>Sintaxe

```
devenv /SafeMode
```

## <a name="remarks"></a>Comentários
 Essa opção impede que todos os VSPackages de terceiros sejam carregados quando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é iniciado, garantindo assim uma execução estável.

## <a name="description"></a>Descrição
 O exemplo a seguir inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no modo de segurança.

## <a name="code"></a>Código

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)