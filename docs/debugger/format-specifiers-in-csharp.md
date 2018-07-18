---
title: Formatar especificadores no depurador (c#) | Microsoft Docs
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
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 0e8605671d1c245826ce6d699e91795fcd7ee32e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756854"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Especificadores de formato em c# no depurador do Visual Studio
Você pode alterar o formato no qual um valor é exibido na **inspeção** janela usando especificadores de formato. Você também pode usar especificadores de formato na **Immediate** janela, o **comando** janela, na [tracepoints](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)e até mesmo em janelas de origem. Se você pausar em uma expressão nessas janelas, o resultado aparecerá em uma DataTip. As DataTips refletirão o especificador de formato na tela DataTip.  
  
 Para usar um especificador de formato, digite a expressão seguida por uma vírgula. Após a vírgula, adicione o especificador apropriado.  
  
## <a name="using-format-specifiers"></a>Usando especificadores de formato  
 Se você tiver o seguinte código:  
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Adicionar o `my_var1` variável à janela Inspeção (durante a depuração, **Depurar > Windows > inspeção > inspecionar 1**) e definir a exibição em hexadecimal (no **inspeção** janela, a variável com o botão direito e Selecione **exibição Hexadecimal**). Agora o **inspeção** janela mostra que ele contém o valor 0x0065. Para ver esse valor, expresso como um inteiro decimal em vez de um inteiro hexadecimal, na coluna Nome, após o nome da variável, adicione o especificador de formato decimal: **, d**. A coluna de valor agora exibe o valor decimal 101  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Especificadores de formato  
 A tabela a seguir exibe os especificadores de formato C# reconhecidos pelo depurador.  
  
|Especificador|Formatar|Valor original de inspeção|Telas|  
|---------------|------------|--------------------------|--------------|  
|CA|Forçar avaliação de uma expressão. Isso pode ser útil quando a avaliação implícita das propriedades e das chamadas de função implícitas é desativada.|"Avaliação da função implícita está desativada pelo usuário" da mensagem|\<value>|  
|d|inteiro decimal|0x0065|101|  
|dinâmica|Exibe o objeto especificado usando um Modo de Exibição Dinâmico|Exibe todos os membros do objeto, incluindo o modo de exibição dinâmico|Exibe apenas o modo de exibição dinâmico|  
|h|inteiro hexadecimal|61541|0x0000F065|  
|nq|cadeia de caracteres sem aspas|"Minha cadeia de caracteres"|Minha cadeia de caracteres|  
|nSe|Especifica o comportamento, não o formato. Avalia a expressão "Sem efeitos colaterais". Se a expressão não pode ser interpretada e só pode ser resolvida por uma avaliação (como uma chamada de função), você verá um erro em vez disso.|N/D|N/D|
|oculto|Exibe todos os membros públicos e não públicos|Exibe os membros públicos|Exibe todos os membros|  
|bruto|Exibe o item como aparece no nó bruto do item. Válido apenas em objetos proxy.|Dicionário\<T >|Modo de exibição bruto do dicionário\<T >|  
|resultados|Usado com uma variável de um tipo que implementa IEnumerable ou IEnumerable\<T >, geralmente o resultado de uma expressão de consulta. Exibe apenas os membros que contém o resultado da consulta.|Exibe todos os membros.|Exibe os membros que atendam as condições da consulta.|  
  
## <a name="see-also"></a>Consulte também  
 [Inspeção e QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Janelas Autos e Locais](../debugger/autos-and-locals-windows.md)
