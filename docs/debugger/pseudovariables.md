---
title: "Pseudovariáveis | Microsoft Docs"
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
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b92b070641e4eed47b0094e1611f78cd799e6952
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudovariáveis no depurador do Visual Studio
Pseudovariáveis são termos usados para exibir certas informações em uma janela variável ou o **QuickWatch** caixa de diálogo. Você pode inserir um pseudovariável da mesma maneira que incorporaria uma variável normal. As pseudovariáveis não são variáveis, no entanto, e não correspondem aos nomes de variáveis em seu programa.  
  
## <a name="example"></a>Exemplo  
 Suponha que você está escrevendo um aplicativo de código nativo e quer consultar o número de identificadores alocados em seu aplicativo. No **inspecionar** janela, você pode inserir as pseudovariáveis a seguir no **nome** coluna e, em seguida, pressione Return para avaliá-lo:  
  
```  
$handles  
```  
  
 em código nativo, você pode usar as pseudovariáveis mostradas na tabela:  
  
|Pseudovariável|Função|  
|--------------------|--------------|  
|`$err`|Exibe o último conjunto de valores de erro com a função SetLastError. O valor que é exibido representa o que seria retornado pela função GetLastError.<br /><br /> Use `$err,hr` para ver o formulário decodificado deste valor. Por exemplo, se o erro mais recente fosse 3, `$err,hr` exibiria `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Exibe o número de manipuladores alocados em seu aplicativo.|  
|`$vframe`|Exibe o endereço do quadro de pilha atual.|  
|`$tid`|Exibe a ID do thread para o thread atual.|  
|`$env`|Exibe o bloco de ambiente no visualizador de cadeia de caracteres.|  
|`$cmdline`|Exibe a cadeia de caracteres de linha de comando que iniciou o programa.|  
|`$pid`|Exibe a identificação do processo.|  
|`$`*registername*<br /><br /> ou<br /><br /> `@`*registername*|Exibe o conteúdo do registro de *registername*.<br /><br /> Normalmente, você pode exibir conteúdo do registro simplesmente inserindo o nome do registro. A única vez que você precisa usar essa sintaxe é quando o nome do registro sobrecarrega um nome de variável. Se o nome do registro for igual ao nome da variável no escopo atual, o depurador interpretará o nome como um nome de variável. Ou seja, quando `$` *registername* ou `@` *registername* é útil.|  
|`$clk`|Exibe a hora em ciclos de relógio.|  
|`$user`|Exibe uma estrutura com informações de conta para a conta que executa o aplicativo. Por motivo de segurança, as informações de senha não são exibidas.|  
|`$exceptionstack`|Exibe o rastreamento de pilha da exceção atual de Tempo de Execução do Windows. `$ exceptionstack`funciona apenas em aplicativos UWP e Windows 8.1 ou posterior. `$ exceptionstack` não tem suporte para exceções de C++ e SHE|  
|`$ReturnValue`|Mostra o valor retornado de um método .NET Framework.|  
  
 No C# e no Visual Basic, você pode usar as pseudovariáveis mostradas na tabela:  
  
|Pseudovariável|Função|  
|--------------------|--------------|  
|`$exception`|Exibe informações sobre a última exceção. Se nenhuma exceção tiver ocorrido, a avaliação `$exception` exibirá uma mensagem de erro.<br /><br /> No Visual c#, quando o Assistente de exceção é desabilitado, `$exception` é adicionado automaticamente para o **locais** janela quando ocorre uma exceção.|  
|`$user`|Exibe uma estrutura com informações de conta para a conta que executa o aplicativo. Por motivo de segurança, as informações de senha não são exibidas.|  
  
 No Visual Basic, você pode usar as pseudovariáveis mostradas na seguinte tabela:  
  
|Pseudovariável|Função|  
|--------------------|--------------|  
|`$delete` ou `$$delete`|Exclui uma variável implícita que foi criada o **imediato** janela. A sintaxe é `$delete,` *variável* ou`$delete,` *variável*`.`|  
|`$objectids` ou `$listobjectids`|Exibe todas as IDs de objetos como filhos da expressão especificada. A sintaxe é `$objectid,` *expressão* ou`$listobjectids,` *expressão*`.`|  
|`$`*N*`#`|Exibe os objetos com a ID de objeto igual a *N*.|  
|`$dynamic`|Exibe o especial **exibição dinâmica** nó para um objeto que implementa o `IDynamicMetaObjectProvider`. Interface. A sintaxe é `$dynamic,` *objeto*. Esse recurso se aplica somente ao código que usa o .NET Framework versão 4.|  
  
## <a name="see-also"></a>Consulte também  
 [Inspecionar e Windows QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Janelas variáveis](../debugger/debugger-windows.md)