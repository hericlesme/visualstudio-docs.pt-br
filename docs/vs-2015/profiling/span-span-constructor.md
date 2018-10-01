---
title: Construtor span::span | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9cd7d787c136f6811fe6bc4c20fe24f736b29e4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466416"
---
# <a name="spanspan-constructor"></a>Construtor span::span
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [SPAN:: SPAN construtor](https://docs.microsoft.com/visualstudio/profiling/span-span-constructor).  
  
Inicializa uma nova instância da classe `span`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
span(  
   const marker_series& _Series,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `_Series`  
 Contexto de série de marcador válido.  
  
 `_Format`  
 Uma cadeia de caracteres de formato de composição, que contém texto intercalado com zero ou mais itens de formato correspondentes a objetos na lista de argumentos.  
  
 `_Importance`  
 Nível de importância.  
  
 `_Category`  
 Categoria.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic
 
 ## <a name="see-also"></a>Consulte também
 [Classe span](../profiling/span-class.md)



