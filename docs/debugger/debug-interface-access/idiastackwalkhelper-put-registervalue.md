---
title: "IDiaStackWalkHelper::put_registerValue | Microsoft Docs"
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
  - "Método IDiaStackWalkHelper2::put_registerValue"
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Define o valor de um registrador.  
  
## Sintaxe  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### Parâmetros  
 `index`  
 \[in\] Um valor a partir do [Enumeração CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md) enumeração que especifica o registro para gravar.  
  
 `NewVal`  
 \[in\] O novo valor do registro.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Apesar do tamanho do valor, uma implementação deve armazenar apenas o que o registro normalmente contém.  Por exemplo, um registrador de 8 bits deveria conter apenas o menor 8 bits de um determinado valor.  
  
## Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeração CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md)