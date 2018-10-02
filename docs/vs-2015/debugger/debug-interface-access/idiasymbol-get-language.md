---
title: 'Idiasymbol:: Get_language | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_language method
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08a4d92a8354c5f7d97d7ee5924a233bcc4cd85d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466475"
---
# <a name="idiasymbolgetlanguage"></a>IDiaSymbol::get_language
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiasymbol:: Get_language](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-language).  
  
Recupera o idioma da fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_language (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna um valor da [enumeração CV_CFL_LANG](../../debugger/debug-interface-access/cv-cfl-lang.md) enumeração que especifica o idioma da fonte.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração CV_CFL_LANG](../../debugger/debug-interface-access/cv-cfl-lang.md)



