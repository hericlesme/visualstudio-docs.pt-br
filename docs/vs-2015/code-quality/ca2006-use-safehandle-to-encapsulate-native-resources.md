---
title: 'CA2006: Use SafeHandle para encapsular recursos nativos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 08eed3577a8c225a69c5a3a8a9b4a1348656bd3f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587155"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: use SafeHandle para encapsular recursos nativos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2006: Use SafeHandle para encapsular recursos nativos](https://docs.microsoft.com/visualstudio/code-quality/ca2006-use-safehandle-to-encapsulate-native-resources).

|||
|-|-|
|NomeDoTipo|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 O código gerenciado usa <xref:System.IntPtr> para acessar recursos nativos.

## <a name="rule-description"></a>Descrição da Regra
 Uso de `IntPtr` em código gerenciado pode indicar um problema potencial de segurança e confiabilidade. Todos os usos da `IntPtr` devem ser examinados para determinar se o uso de um <xref:System.Runtime.InteropServices.SafeHandle> , ou uma tecnologia semelhante, é necessário em seu lugar. Problemas ocorrerão se o `IntPtr` representa algum recurso nativo, como memória, um identificador de arquivo ou um soquete, que o código gerenciado é considerado como o próprio. Se o código gerenciado tem o recurso, ele também deve liberar os recursos nativos associados a ela, porque uma falha ao fazer isso causaria perda de recursos.

 Nesses cenários, problemas de segurança ou confiabilidade também existirá se o acesso com multithread é permitido para o `IntPtr` e uma maneira de liberar o recurso que é representado pelo `IntPtr` é fornecido. Esses problemas que envolvem a reciclagem do `IntPtr` valor na liberação de recursos enquanto o uso simultâneo do recurso está sendo feito em outro thread. Isso pode causar condições de corrida em que um thread pode ler ou gravar dados que está associados com o recurso incorreto. Por exemplo, se seu tipo armazena um identificador de sistema operacional como um `IntPtr` e permite que os usuários que ambos **fechar** e qualquer outro método que usa esse identificador ao mesmo tempo e sem algum tipo de sincronização, o código tem um reciclagem de identificador problema.

 Esse problema de reciclagem de identificador pode causar corrupção de dados e, frequentemente, uma vulnerabilidade de segurança. `SafeHandle` e sua classe irmão <xref:System.Runtime.InteropServices.CriticalHandle> fornecem um mecanismo para encapsular um identificador nativo para um recurso, de modo que esses problemas de threading podem ser evitados. Além disso, você pode usar `SafeHandle` e sua classe irmão `CriticalHandle` para outros problemas de threading, por exemplo, para controlar o tempo de vida de objetos gerenciados que contêm uma cópia do identificador nativo em chamadas a métodos nativos com cuidado. Nessa situação, geralmente, você pode remover chamadas para `GC.KeepAlive`. O tailandês de sobrecarga de desempenho você provoca quando você usa `SafeHandle` e, em um grau menor, `CriticalHandle`, com frequência pode ser reduzido por meio de um design cuidadoso.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Converter `IntPtr` uso para `SafeHandle` para gerenciar com segurança o acesso aos recursos nativos. Consulte o <xref:System.Runtime.InteropServices.SafeHandle> tópico de referência para obter exemplos.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você não deve suprimir esse aviso.

## <a name="see-also"></a>Consulte também
 <xref:System.IDisposable>



