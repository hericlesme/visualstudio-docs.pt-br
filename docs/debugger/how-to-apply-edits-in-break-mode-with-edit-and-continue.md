---
title: 'Como: aplicar edições no modo de interrupção com editar e continuar | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f031598e0c8f290907e759bcfceac85c1b063f5f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474187"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Como aplicar edições no modo de interrupção com editar e continuar
Você pode usar Editar e Continuar para editar o código no modo de interrupção e, depois, continuar sem interromper e reiniciar a execução.  
  
Para limitações sobre o uso de editar e continuar durante a depuração, consulte [suporte para alterações de código (c# e Visual Basic](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>Para editar código no modo de interrupção  
  
1.  Entre no modo de interrupção executando um destes procedimentos:  
  
    -   Definir um ponto de interrupção no seu código, em seguida, escolha **iniciar depuração** do **depurar** menu e aguarde o aplicativo para o ponto de interrupção.  
  
         -ou-  
  
    -   Iniciar a depuração e, em seguida, selecione **interromper tudo** do **depurar** menu.  
  
         -ou-  
  
    -   Quando ocorre uma exceção, escolha **habilitar edição** no**Exception Assistant**.  
  
2.  Faça as alterações de código desejadas e com suporte.  
  
     Para obter mais informações, consulte [suporte para alterações de código (c# e Visual Basic](../debugger/supported-code-changes-csharp.md).  
  
    > [!NOTE]
    >  Se você tentar fazer uma alteração de código que não seja permitida por Editar e Continuar, sua edição será sublinhada por uma linha ondulada roxa e uma tarefa será exibida na Lista de Tarefas. Você não poderá continuar a execução do código a menos que desfaça a alteração de código ilegal.  
  
3.  Sobre o **depurar** menu, clique em **continuar** para retomar a execução.  
  
     O código agora é executado com as edições aplicadas incorporadas ao projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de código suportadas (c# e Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [Editar e Continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)