---
title: Estruturas do Visual C++ no Designer de Classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: d0621b5a2a82786a41e8d566954f03341affa905
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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