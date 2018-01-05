---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-method
title: "Extrair método refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 18fc4c20b39341f884fb23b51822ce7f6e427007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-method-refactoring-c"></a>Refatoração Extrair Método (C#)
**Extrair método** é uma operação de refatoração que fornece uma maneira fácil de criar um novo método de um fragmento de código em um membro existente.  
  
 Usando **extrair método**, você pode criar um novo método extraindo uma seleção de código de dentro do bloco de código de um membro existente. O método extraído, novo contém o código selecionado, e o código selecionado no membro existente é substituído por uma chamada para o novo método. Transformar um fragmento de código em seu próprio método permite que você rapidamente e reorganizar com precisão o código para melhorar a legibilidade e reutilização.  
  
 **Extrair método** tem os seguintes benefícios:  
  
-   Incentiva práticas de codificação melhor ressaltando métodos discretos, reutilizáveis.  
  
-   Incentiva autodescritivo código por meio de organização válido.  
  
     Quando nomes descritivos são usados e de alto nível métodos podem ler mais como uma série de comentários.  
  
-   Incentiva a criação de métodos refinado para simplificar a substituição.  
  
-   Reduz a duplicação de código.  
  
### <a name="to-use-extract-method"></a>Use extrair método  
  
1.  Criar um aplicativo de console chamado `ExtractMethod`e, em seguida, substitua `Program` com o código de exemplo a seguir.  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  Selecione o fragmento de código que você deseja extrair:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  Sobre o **refatorar** menu, clique em **extrair método**.  
  
     O **extrair método** caixa de diálogo é exibida.  
  
     Como alternativa, você também pode digitar o atalho de teclado CTRL + R, M para exibir o **extrair método** caixa de diálogo.  
  
     Você pode também clique selecionado de código, aponte para **refatorar**e, em seguida, clique em **extrair método** para exibir o **extrair método** caixa de diálogo.  
  
4.  Especifique um nome para o novo método, como `CircleArea`, além de **novo nome do método** caixa.  
  
     Exibe uma visualização da nova assinatura de método em **Visualizar assinatura do método**.  
  
5.  Clique em **OK**.  
  
## <a name="remarks"></a>Comentários  
 Quando você usa o **extrair método** de comando, o novo método é inserido após o membro de origem na mesma classe.  
  
## <a name="partial-types"></a>Tipos parciais  
 Se a classe for um tipo parcial, em seguida, **extrair método** gera o novo método imediatamente após o membro de origem. **Extrair método** determina a assinatura do método novo, criar um método estático quando não há dados de instância são referenciados pelo código no método de novo.  
  
## <a name="generic-type-parameters"></a>Parâmetros de tipo genérico  
 Quando você extrai um método que tem um parâmetro de tipo genérico não restrita, o código gerado não adicionará o `ref` modificador para esse parâmetro, a menos que um valor é atribuído a ele. Se o método extraído dará suporte a tipos de referência como o argumento de tipo genérico, você deve adicionar manualmente o `ref` modificador de parâmetro na assinatura do método.  
  
## <a name="anonymous-methods"></a>Métodos anônimos  
 Se você tentar extrair parte de um método anônimo que inclui uma referência a uma variável local declarada ou referenciada fora do método anônimo, em seguida, o Visual Studio avisará sobre possíveis alterações semânticas.  
  
 Quando um método anônimo usa o valor de uma variável local, o valor é obtido no momento em que o método anônimo é executado. Quando um método anônimo é extraído no outro método, o valor da variável local é obtido no momento da chamada para o método extraído.  
  
 O exemplo a seguir ilustra essa alteração semântica. Se esse código é executado, em seguida, **11** será impressa no console. Se você usar **extrair método** para extrair a região de código que é marcado por comentários de código em seu próprio método e, em seguida, execute o código refatorado, em seguida, **10** será impressa no console.  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 Para solucionar essa situação, verifique as variáveis locais que são usadas nos campos de um método anônimo, da classe.  
  
## <a name="see-also"></a>Consulte também  
 [Refatoração (C#)](refactoring-csharp.md)