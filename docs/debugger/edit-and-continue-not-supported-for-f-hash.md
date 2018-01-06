---
title: "Editar e continuar não suportado para F # | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 290b144da6cf6c8e680fdba7dcf99ffbaa19cf53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="edit-and-continue-not-supported-for-f"></a>Editar e Continuar não suportado para F# #
A função Editar e Continuar não tem suporte quando você depura o código F#. As edições ao código F# são possíveis durante uma sessão de depuração mas devem ser evitadas. As alterações de código não são aplicadas durante a sessão de depuração. Como consequência, todas as edições feitas no código F# enquanto você depura resultarão no código-fonte que não corresponde ao código que está sendo depurado.
