---
title: 'CA1400: Pontos de entrada P Invoke devem existir'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36bd2e74b5abb021b66dda8ddd62260cc58fe181
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: os pontos de entrada P/Invoke devem existir
|||
|-|-|
|NomeDoTipo|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um método público ou protegido é marcado com o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Não foi possível localizar a biblioteca não gerenciada ou não foi possível comparar o método a uma função na biblioteca. Se a regra não é possível localizar o nome do método exatamente como ele é especificado, ele procura por ANSI ou versões de caractere largo do método, adicionando o nome do método com 'A' ou 'W'. Se nenhuma correspondência for encontrada, a regra tenta localizar uma função usando o formato de nome stdcall (_MyMethod@12, onde 12 representa o comprimento dos argumentos). Se nenhuma correspondência for localizada, e o nome do método começa com '#', a regra de pesquisa para a função como uma referência ordinal em vez de uma referência de nome.

## <a name="rule-description"></a>Descrição da Regra
 Não há verificação de tempo de compilação está disponível para certificar-se de que os métodos que são marcados com <xref:System.Runtime.InteropServices.DllImportAttribute> estão localizados na DLL não gerenciada referenciada. Se nenhuma função que tem o nome especificado está na biblioteca, ou os argumentos para o método não coincidem com os argumentos da função, o common language runtime lançará uma exceção.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, corrija o método que tem o <xref:System.Runtime.InteropServices.DllImportAttribute> atributo. Certifique-se de que a biblioteca não gerenciada existe e está no mesmo diretório que o assembly que contém o método. Se a biblioteca estiver presente e referenciado corretamente, verifique se o nome do método, o tipo de retorno e a assinatura de argumento correspondem a função de biblioteca.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso dessa regra quando a biblioteca não gerenciada está no mesmo diretório que o assembly gerenciado que faz referência a ele. Talvez seja seguro suprimir um aviso dessa regra no caso em que a biblioteca não gerenciada não pôde ser localizada.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra. Nenhuma função chamada `DoSomethingUnmanaged` ocorre no Kernel32. dll.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>