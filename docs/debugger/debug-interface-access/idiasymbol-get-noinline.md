---
title: "IDiaSymbol::get_noInline | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Método IDiaSymbol::get_noInline"
ms.assetid: 5c610b78-f1a3-494a-acf8-c42b97935be1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_noInline
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um sinalizador que especifica se a função foi marcada como não sendo in\-line \(usando o [noinline](/visual-cpp/cpp/noinline) atributo\).  
  
## Sintaxe  
  
```cpp  
HRESULT get_noInline(  
   BOOL *pFlag  
);  
```  
  
#### Parâmetros  
 `pFlag`  
 \[out\] Retorna `TRUE` se a função tem a `noinline` de atributo; Caso contrário, retornará `FALSE`.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Requisitos  
  
|Requisito|Descrição|  
|---------------|---------------|  
|Cabeçalho:|dia2.h|  
|Versão:|V 8.0 do SDK DIA|  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [noinline](/visual-cpp/cpp/noinline)