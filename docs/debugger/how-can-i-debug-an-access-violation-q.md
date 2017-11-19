---
title: "Como depurar uma violação de acesso C++? | Microsoft Docs"
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93b7a670d74fbbb0c9d8e13f1e6463b52a8ca5d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Como depurar uma violação de acesso C++?
## <a name="problem-description"></a>Descrição do problema  
 Meu programa produz uma violação de acesso. Como posso depurar isso?  
  
## <a name="solution"></a>Solução  
 Se você receber uma violação de acesso em uma linha de código que cancela a referência de vários ponteiros, pode ser difícil descobrir quais ponteiro causou a violação de acesso. A partir do Visual Studio 2015 atualização 1, a caixa de diálogo de exceção agora explicitamente nomeia o ponteiro que causou a violação de acesso.  
  
 Por exemplo, dado o código a seguir, você deve obter uma violação de acesso:  
  
```C++  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
        ClassC* C;  
        ClassB() {  
                C = new ClassC();  
        }  
     void printHello() {  
                cout << "hello world";  
        }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
      ClassA() {  
                B = nullptr;  
        }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
      A->B->printHello();  
}  
```  
  
 Se você executar esse código no Visual Studio 2015 atualização 1, você verá a seguinte caixa de diálogo de exceção:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Se você não puder determinar por que o ponteiro causou uma violação de acesso, o rastreamento através do código para certificar-se de que o ponteiro causando o problema foi atribuído corretamente.  Se ele é passado como um parâmetro, certifique-se de que ela será transmitida corretamente e você não criar acidentalmente um [shallow cópia](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Verifique se que os valores não sejam sendo acidentalmente alterados em algum lugar no programa criando um ponto de interrupção de dados para o ponteiro em questão para certificar-se de que ele não está sendo modificado em outro lugar no programa. Para obter mais informações sobre pontos de interrupção de dados, consulte a seção de ponto de interrupção de dados em [usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes de depuração de código nativo](../debugger/debugging-native-code-faqs.md)