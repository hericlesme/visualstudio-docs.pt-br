---
title: Estruturas do Visual C++ no Designer de Classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6f2aa3893a230abd52dd5cf19ed9d751e56e50c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-structures-in-class-designer"></a>Estruturas do Visual C++ no Designer de Classe
O Designer de Classe dá suporte a estruturas C++ declaradas com a palavra-chave `struct`. Veja um exemplo a seguir:  
  
```cpp
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
Para obter mais informações sobre o uso do tipo `struct`, consulte [struct](/cpp/cpp/struct-cpp).  
  
Uma forma de estrutura C++ em um diagrama de classe parece uma forma de classe e funciona como uma, exceto que o rótulo lê **Struct** e tem cantos quadrados em vez de arredondados.  
  
|Elemento de código|Modo de exibição do Designer de Classe|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Estrutura|  
  
## <a name="see-also"></a>Consulte também
[Trabalhando com o Visual C++ Code](working-with-visual-cpp-code.md)   
[Classes e structs](/cpp/cpp/classes-and-structs-cpp)   
[struct](/cpp/cpp/struct-cpp)