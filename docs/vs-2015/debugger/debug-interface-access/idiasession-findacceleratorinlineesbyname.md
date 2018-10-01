---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
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
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1bda42ce7f33887460666e3ae8c0e8956003914b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47461912"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDiaSession::findAcceleratorInlineesByName](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname).  
  
Retorna uma enumeração de símbolos para quadros embutidos correspondente ao nome da função especificados em linha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 [in] O nome da função de item embutido a ser pesquisado.  
  
 `option`  
 [in] As opções de pesquisa de nome a ser usado ao pesquisar embutido quadros que correspondem aos `name`. Para obter mais informações, consulte [enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Um ponteiro para um `IDiaEnumSymbols` ponteiro de interface que é inicializado com o resultado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Essa função pesquisa itens embutidos somente em funções de stub do acelerador. Ele ignora os registros de procedimento de C++ nativos.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



