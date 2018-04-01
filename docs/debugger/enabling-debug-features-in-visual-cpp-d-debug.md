---
title: Habilitando recursos de depuração no Visual C++ (-/d_debug) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f1067ee5b60b8a8a402c9612357f2d83b6da138
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Habilitando funcionalidades de depuração no Visual C++ (/D_DEBUG)
Em [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], recursos de depuração, como as declarações são habilitadas quando você compila seu programa com o símbolo **Debug** definido. Você pode definir **Debug** em uma das duas maneiras:  
  
-   Especifique **#define Debug** em seu código-fonte, ou  
  
-   Especifique o **/D_DEBUG** opção de compilador. (Se você criar seu projeto no Visual Studio usando assistentes, **/D_DEBUG** é definido automaticamente na configuração de depuração.)  
  
 Quando **Debug** é definido, o compilador compila seções de código cercado por **#ifdef DEBUG** e `#endif`.  
  
 A configuração Depuração de um programa MFC deve ser vinculada a uma versão de depuração da biblioteca MFC. Os arquivos de cabeçalho MFC determinam a versão correta da biblioteca MFC para vincular com baseada nos símbolos que você definiu, tais como **Debug** e **Unicode**. Para obter detalhes, consulte [versões de biblioteca MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código nativo](../debugger/debugging-native-code.md)   
 [Configurações do projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)