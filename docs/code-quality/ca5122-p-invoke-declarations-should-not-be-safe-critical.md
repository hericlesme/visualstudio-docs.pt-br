---
title: 'P-Invoke ca5122: declarações não devem ser seguras crítico'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e73af173dd7e82a139c204051c72480a50e38fa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122: declarações P/Invoke não devem ser críticas para segurança
|||
|-|-|
|NomeDoTipo|PInvokesShouldNotBeSafeCriticalFxCopRule|
|CheckId|CA5122|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma declaração P/Invoke foi marcada com <xref:System.Security.SecuritySafeCriticalAttribute>:

```csharp
[assembly: AllowPartiallyTrustedCallers]

// ...
public class C
{
    [SecuritySafeCritical]
    [DllImport("kernel32.dll")]
    public static extern bool Beep(int frequency, int duration); // CA5122 - safe critical p/invoke
   }

```

 Neste exemplo, `C.Beep(...)` foi marcado como um método crítico de segurança.

## <a name="rule-description"></a>Descrição da Regra
 Os métodos são marcados como SecuritySafeCritical quando executam uma operação confidencial de segurança, mas também são seguros para serem usados pelo código transparente. Uma das regras básicas do modelo de transparência de segurança é que o código transparente nunca pode chamar diretamente o código nativo por P/Invoke. Por isso, a marcação de um P/Invoke como crítico de segurança não permitirá que o código transparente o chame, e é enganosa na análise de segurança.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para tornar P/Invoke disponível para o código transparente, exponha um método wrapper crítico de segurança para ele:

```csharp
[assembly: AllowPartiallyTrustedCallers

class C
{
   [SecurityCritical]
   [DllImport("kernel32.dll", EntryPoint="Beep")]
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke

   [SecuritySafeCritical]
   public static bool Beep(int frequency, int duration)
   {
      return BeepPInvoke(frequency, duration);
   }
}

```

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.