---
title: 'CA2115: chamar GC.KeepAlive durante o uso de recursos nativos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 66621bec3316dfcee92a1e5b1d1d1a8d97ae5c54
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914647"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: chamar GC.KeepAlive durante o uso de recursos nativos
|||
|-|-|
|NomeDoTipo|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Um método declarado em um tipo com um finalizador faz referência a um <xref:System.IntPtr?displayProperty=fullName> ou <xref:System.UIntPtr?displayProperty=fullName> campo, mas não chama <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 Coleta de lixo Finaliza um objeto se não houver nenhuma mais referências a ele em código gerenciado. Não gerenciadas referências a objetos não impedem que a coleta de lixo. Esta regra detecta erros que podem ocorrer porque um recurso não gerenciado está sendo finalizado, enquanto ainda está sendo usado em código não gerenciado.

 Essa regra supõe que <xref:System.IntPtr> e <xref:System.UIntPtr> campos armazenam ponteiros para os recursos não gerenciados. Como é a finalidade de um finalizador liberar recursos não gerenciados, a regra pressupõe que o finalizador irá liberar o recurso não gerenciado que aponta para os campos de ponteiro. Esta regra também pressupõe que o método está referenciando o campo de ponteiro para passar o recurso não gerenciado para código não gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, adicione uma chamada para <xref:System.GC.KeepAlive%2A> para o método, passando a instância atual (`this` em c# e C++) como o argumento. Posicione a chamada após a última linha do código onde o objeto deve ser protegido da coleta de lixo. Imediatamente após a chamada a <xref:System.GC.KeepAlive%2A>, o objeto será considerado novamente pronto para coleta de lixo supondo que não haja nenhuma referência gerenciada para ele.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Essa regra faz algumas suposições que podem resultar em falsos positivos. Com segurança, você pode suprimir um aviso de que essa regra se:

-   O finalizador não libera o conteúdo a <xref:System.IntPtr> ou <xref:System.UIntPtr> campo referenciado pelo método.

-   O método não passa a <xref:System.IntPtr> ou <xref:System.UIntPtr> campo para código não gerenciado.

 Leia com atenção as outras mensagens antes de excluí-las. Essa regra detecta erros que são difíceis de reproduzir e depurar.

## <a name="example"></a>Exemplo
 No exemplo a seguir, `BadMethod` não inclui uma chamada para `GC.KeepAlive` e, portanto, viola a regra. `GoodMethod` contém o código corrigido.

> [!NOTE]
>  Este exemplo é pseudocódigo, embora o código compila e executa, o aviso não é acionado porque um recurso não gerenciado não é criado ou liberado.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Consulte também
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName> <xref:System.Object.Finalize%2A?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName> [Padrão de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)