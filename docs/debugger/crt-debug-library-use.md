---
title: "Uso da biblioteca de depuração CRT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2774eacfb0472145edb84d5c3becf77513ee986
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="crt-debug-library-use"></a>Uso da biblioteca de depuração CRT
A biblioteca em tempo de execução C fornece amplo suporte à depuração. Para usar uma das bibliotecas de depuração CRT, você deve vincular com [/Debug](/cpp/build/reference/debug-generate-debug-info) e compile com **/MDd**, **/MTd**, ou **/LDd**.  
  
## <a name="remarks"></a>Comentários  
 As definições e macros principais de depuração de CRT podem ser encontradas no arquivo de cabeçalho CRTDBG.h.  
  
 As funções nas bibliotecas de depuração CRT são compiladas com informações de depuração ([/Z7, /Zd, /Zi, /ZI (Depurar formato de informações)](/cpp/build/reference/z7-zi-zi-debug-information-format)) e sem otimização. Algumas funções contêm asserções para verificar os parâmetros passados a elas, e o código-fonte será fornecido. Com esse código-fonte, você pode acessar funções de CRT para confirmar se as funções estão funcionando conforme o esperado e verificar se há parâmetros incorretos ou estados de memória. (Qualquer tecnologia de CRT é proprietária e não fornece código-fonte para tratamento de exceções, ponto flutuante e algumas outras rotinas.)  
  
 Quando você instalar o Visual C++, terá a opção de instalar o código-fonte da biblioteca em tempo de execução C no disco rígido. Se você não instalar o código-fonte, precisará do CD-ROM para acessar as funções de CRT.  
  
 Para obter mais informações sobre as várias bibliotecas de tempo de execução, você pode usar, consulte [bibliotecas em tempo de execução C](/cpp/c-runtime-library/crt-library-features).  
  
## <a name="see-also"></a>Consulte também  
 [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (usar biblioteca de tempo de execução)](/cpp/build/reference/md-mt-ld-use-run-time-library)