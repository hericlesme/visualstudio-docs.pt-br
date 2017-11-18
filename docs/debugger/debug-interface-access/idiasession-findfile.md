---
title: ': FindFile | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef230d1b82992f769011e0cb1d9d4ff11145b82d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Recupera os arquivos de origem pelo nome e compiland.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCompiland`  
 [in] Um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa o compiland a ser usado como um contexto para a pesquisa. Definir esse parâmetro como `NULL` para localizar arquivos de origem em todos os compilandos.  
  
 `name`  
 [in] Especifica o nome do arquivo de origem a serem recuperados. Definir esse parâmetro como `NULL` para todos os arquivos a serem recuperados de origem.  
  
 `option`  
 [in] Especifica as opções de comparação aplicadas à pesquisa de nome. Os valores do [enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumeração pode ser usada sozinha ou em combinação.  
  
 `ppResult`  
 [out] Retorna um [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) recuperado do objeto que contém uma lista dos arquivos de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)