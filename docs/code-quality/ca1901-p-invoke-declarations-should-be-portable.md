---
title: "CA1901: Declarações P Invoke devem ser portáteis | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6e0d3ce3d0130b0a2cf40f6d4f1716c32ae7c40e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: as declarações de P/Invoke devem ser portáteis
|||  
|-|-|  
|NomeDoTipo|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Categoria|Microsoft.Portability|  
|Alteração Significativa|Quebrar - se a P/Invoke é visível fora do assembly. Não separáveis - se a P/Invoke não é visível fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Essa regra avalia o tamanho de cada parâmetro e o valor de retorno de um P/Invoke e verifica se o seu tamanho, quando passa por marshaling para código não gerenciado em plataformas de 32 bits e 64 bits, está correto. É a violação mais comum dessa regra passar um inteiro de tamanho fixo onde a variável dependente de plataforma, o tamanho de ponteiro é necessária.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Qualquer um dos seguintes cenários viola essa regra ocorre:  
  
-   O valor de retorno ou parâmetro é digitado como um inteiro de tamanho fixo quando ele deve ser digitado como um `IntPtr`.  
  
-   O valor de retorno ou parâmetro é digitado como um `IntPtr` quando ele deve ser digitado como um inteiro de tamanho fixo.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Você pode corrigir essa violação usando `IntPtr` ou `UIntPtr` representar identificadores em vez de `Int32` ou `UInt32`.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Você não deve suprimir este aviso.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra uma violação desta regra.  
  
```csharp  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 Neste exemplo, o `nIconIndex` parâmetro seja declarado como um `IntPtr`, que é de 4 bytes de largura em uma plataforma de 32 bits e de 8 bytes de largura em uma plataforma de 64 bits. A declaração não gerenciada que segue, você verá que `nIconIndex` é um inteiro sem sinal de 4 bytes em todas as plataformas.  
  
```csharp  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## <a name="example"></a>Exemplo  
 Para corrigir a violação, altere a declaração para o seguinte:  
  
```csharp  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Avisos de portabilidade](../code-quality/portability-warnings.md)