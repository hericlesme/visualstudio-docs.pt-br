---
title: Formatar especificadores no depurador (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edb41f8fea8447f8616b4c20f442ffd4fa8b48c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Especificadores de formato em c# no depurador do Visual Studio
Você pode alterar o formato no qual um valor é exibido no **inspecionar** janela usando especificadores de formato. Você também pode usar os especificadores de formato no **imediato** janela, o **comando** janela e até mesmo no windows de origem. Se você pausar em uma expressão nessas janelas, o resultado aparecerá em uma DataTip. As DataTips refletirão o especificador de formato na tela DataTip.  
  
 Para usar um especificador de formato, digite a expressão seguida por uma vírgula. Após a vírgula, adicione o especificador apropriado.  
  
## <a name="using-format-specifiers"></a>Usando especificadores de formato  
 Se você tiver o código a seguir:  
  
```CSharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Adicionar o `my_var1` variável à janela de inspeção (durante a depuração, **Depurar > Windows > Observação > inspecionar 1**) e definir a exibição em hexadecimal (no **inspecionar** janela, clique a variável e Selecione **exibição Hexadecimal**). Agora o **inspecionar** janela mostra que ele contém o valor 0x0065. Para ver esse valor, expresso como um inteiro decimal em vez de um número inteiro hexadecimal, na coluna Nome, após o nome da variável, adicione o especificador de formato decimal: **, d**. A coluna de valor agora mostra o valor decimal 101  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Especificadores de formato  
 A tabela a seguir exibe os especificadores de formato C# reconhecidos pelo depurador.  
  
|Especificador|Formatar|Valor original de inspeção|Telas|  
|---------------|------------|--------------------------|--------------|  
|CA|Forçar avaliação de uma expressão. Isso pode ser útil quando a avaliação implícita das propriedades e das chamadas de função implícitas é desativada.|"Avaliação da função implícita está desativada pelo usuário" da mensagem|\<valor >|  
|d|inteiro decimal|0x0065|101|  
|dinâmica|Exibe o objeto especificado usando um Modo de Exibição Dinâmico|Exibe todos os membros do objeto, incluindo o modo de exibição dinâmico|Exibe apenas o modo de exibição dinâmico|  
|h|inteiro hexadecimal|61541|0x0000F065|  
|nq|cadeia de caracteres sem aspas|"Minha cadeia de caracteres"|Minha cadeia de caracteres|  
|oculto|Exibe todos os membros públicos e não públicos|Exibe os membros públicos|Exibe todos os membros|  
|bruto|Exibe o item como aparece no nó bruto do item. Válido apenas em objetos proxy.|Dicionário\<T >|Modo de exibição bruto do dicionário\<T >|  
|resultados|Usado com uma variável de um tipo que implementa IEnumerable ou IEnumerable\<T >, normalmente o resultado de uma expressão de consulta. Exibe apenas os membros que contém o resultado da consulta.|Exibe todos os membros.|Exibe os membros a atendam as condições da consulta.|  
  
## <a name="see-also"></a>Consulte também  
 [Inspecionar e Windows QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Janelas Autos e Locais](../debugger/autos-and-locals-windows.md)
