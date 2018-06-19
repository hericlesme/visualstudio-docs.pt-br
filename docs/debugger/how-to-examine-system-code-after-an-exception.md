---
title: 'Como: Examine o código do sistema após uma exceção | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8a1da63e47514771a868b69ee798f71265fdb42
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472459"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Como examinar um código de sistema após uma exceção
Quando uma exceção ocorre, você poderá precisar examinar o código dentro de uma chamada do sistema para determinar a causa da exceção. O procedimento a seguir explica como fazer isso se você não tiver os símbolos carregados para o código do sistema ou se Just My Code estiver habilitado.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Para examinar o código do sistema após uma exceção  
  
1.  No **pilha de chamadas** janela, clique com botão direito, em seguida, clique em **Mostrar código externo**.  
  
     Se Just My Code não estiver habilitado, essa opção não estará disponível no menu de atalho e o código do sistema será mostrado por padrão.  
  
2.  Clique com botão direito os quadros de código externo que agora aparecem no **pilha de chamadas** janela.  
  
3.  Aponte para **carregar símbolos de** e, em seguida, clique em **Microsoft Symbol Servers**.  
  
    1.  Se Just My Code tiver sido habilitado, uma caixa de diálogo será exibida. Indica que Just My Code agora foi desabilitado. Isso é necessário para entrar em chamadas do sistema.  
  
    2.  O **Baixando símbolos públicos** caixa de diálogo é exibida. Ela desaparecerá quando o download for concluído.  
  
4.  Agora você pode examinar o código de sistema de **pilha de chamadas** janela e outras janelas. Por exemplo, você pode clicar duas vezes um quadro de pilha de chamadas para exibir o código em uma fonte ou **desmontagem** janela.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)