---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-interface
title: "Extrair Interface refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e3e606a86f5989ca928e0b093b564f997f92a559
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-interface-refactoring-c"></a>Refatoração Extrair Interface (C#)
Extrair Interface é uma operação de refatoração que fornece uma maneira fácil de criar uma nova interface com membros que se originam em uma classe existente, struct ou interface.  
  
 Quando vários clientes usam o mesmo subconjunto de membros de uma classe, struct ou interface, ou quando várias classes, estruturas ou interfaces tem um subconjunto de membros em comum, ele pode ser útil para incorporam o subconjunto de membros em uma interface. Para obter mais informações sobre como usar interfaces, consulte [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Extrair Interface gera uma interface em um novo arquivo e posiciona o cursor no início do novo arquivo. Você pode especificar quais membros para extrair para a nova interface, o nome da nova interface e o nome do arquivo gerado usando o **extrair Interface** caixa de diálogo.  
  
### <a name="to-use-extract-interface"></a>Use extrair Interface  
  
1.  Criar um aplicativo de console chamado `ExtractInterface`e, em seguida, substitua `Program` com o código a seguir  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Com o cursor posicionado em `MethodB`e clique em **extrair Interface** no **refatorar** menu.  
  
     O **extrair Interface** caixa de diálogo é exibida.  
  
     Você também pode digitar o atalho de teclado CTRL + R, para exibir o **extrair Interface** caixa de diálogo.  
  
     Você pode também com o botão direito do mouse, aponte para **refatorar**e, em seguida, clique em **extrair Interface** para exibir o **extrair Interface** caixa de diálogo.  
  
3.  Clique em **Selecionar tudo**.  
  
4.  Clique em **OK**.  
  
     Você verá o novo arquivo, IProtoA.cs e o código a seguir:  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>Comentários  
 Este recurso só está acessível quando o cursor é posicionado na classe, struct ou interface que contém os membros que você deseja extrair. Quando o cursor está nessa posição, invocar a operação de refatoração Extrair Interface.  
  
 Quando você chama extrair interface em uma classe ou em uma estrutura, a lista de bases e interfaces é modificada para incluir o novo nome da interface. Quando você chama extrair interface em uma interface, a lista de bases e interfaces não é modificada.  
  
## <a name="see-also"></a>Consulte também  
 [Refatoração (C#)](refactoring-csharp.md)