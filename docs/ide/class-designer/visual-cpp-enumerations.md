---
title: "Enumerações do Visual C++ no Designer de Classe | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad55c68e16fcd340d69178dc24a4b92cada9e2f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-enumerations-in-class-designer"></a>Enumerações do Visual C++ no Designer de Classe
O Designer de Classe oferece suporte ao `enum` do C++ e a tipos `enum class` de escopo. Veja um exemplo a seguir:  
  
```cpp
enum CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
// or...  
enum class CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};
```  
  
Uma forma de enumeração do C++ em um diagrama de classes parece e funciona como uma forma de estrutura, exceto pelo seguinte: o rótulo exibe **Enum** ou **Enum class**, ele é rosa em vez de azul e tem uma borda colorida nas margens esquerda e superior. As formas de enumeração e formas de estrutura tem cantos quadrados.  
  
Para obter mais informações sobre o uso do tipo `enum`, consulte [Enumerações](/cpp/cpp/enumerations-cpp).  
  
## <a name="see-also"></a>Consulte também
[Trabalhando com o Visual C++ Code](working-with-visual-cpp-code.md)   
[Enumerações](/cpp/cpp/enumerations-cpp)