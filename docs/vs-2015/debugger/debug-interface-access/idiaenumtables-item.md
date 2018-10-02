---
title: 'Idiaenumtables:: item | Microsoft Docs'
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
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea80cbcda60b54f17e79e492c43058579465ad90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467510"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiaenumtables:: item](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumtables-item).  
  
Recupera uma tabela por meio de um índice ou nome.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `index`  
 [in] Índice ou nome da [IDiaTable](../../debugger/debug-interface-access/idiatable.md) a ser recuperado. Se uma variante integer for usada, ele deve estar no intervalo de 0 a `count`-1, onde `count` são retornados pelo [idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) método.  
  
 `table`  
 [out] Retorna um [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objeto que representa a tabela desejada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se uma variante de cadeia de caracteres for especificada, a cadeia de caracteres nomeia uma tabela específica. O nome deve ser um dos nomes de tabela conforme definido em [constantes (SDK Interface de depuração acesso)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Exemplo  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Constantes (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)



