---
title: Habilitando recursos de depuração no Visual C++ (-/d_debug) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 5298879d93bf4e86df7610d5891e73bdbb67c4a1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
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