---
title: Como posso depurar uma violação de acesso? | Microsoft Docs
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
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c06121d84c6b573b5f1895fa447535826dad540
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467335"
---
# <a name="how-can-i-debug-an-access-violation"></a>Como posso depurar uma violação de acesso?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como depurar uma violação de acesso?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-debug-an-access-violation-q).  
  
Descrição do problema  
 Meu programa produz uma violação de acesso. Como posso depurar isso?  
  
## <a name="solution"></a>Solução  
 Se você receber uma violação de acesso em uma linha de código que cancela a referência de vários ponteiros, pode ser difícil descobrir quais ponteiro causou a violação de acesso. A partir do Visual Studio 2015 atualização 1, a caixa de diálogo de exceção agora explicitamente nomeia o ponteiro que causou a violação de acesso.  
  
 Por exemplo, dado o código a seguir, você deve obter uma violação de acesso:  
  
```cpp  
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
  
 Se você executar esse código no Visual Studio 2015 atualização 1, você deverá ver a seguinte caixa de diálogo de exceção:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Se você não puder determinar por que o ponteiro causou uma violação de acesso, rastrear o código para certificar-se de que o ponteiro causando o problema foi atribuído corretamente.  Se ele é passado como um parâmetro, certifique-se de que ele é passado corretamente, e você não criar acidentalmente um [cópia superficial](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Em seguida, verifique se que os valores não sejam sendo inadvertidamente alterados em algum lugar no programa, criando um ponto de interrupção de dados para o ponteiro em questão para certificar-se de que não está sendo modificada em outro lugar no programa. Para obter mais informações sobre pontos de interrupção de dados, consulte a seção de ponto de interrupção de dados no [usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes de depuração de código nativo](../debugger/debugging-native-code-faqs.md)



