---
title: 'CA5350: Não Use algoritmos criptográficos fracos'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4426178f7af436f571c7de1b1abce09d4e4d6a5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Não Use algoritmos criptográficos fracos
|||
|-|-|
|NomeDoTipo|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Categoria|Microsoft.Cryptography|
|Alteração Significativa|Não separáveis|

> [!NOTE]
>  Esse aviso última atualização de novembro de 2015.

## <a name="cause"></a>Causa
 Os algoritmos de criptografia, como <xref:System.Security.Cryptography.TripleDES> e algoritmos de hash como <xref:System.Security.Cryptography.SHA1> e <xref:System.Security.Cryptography.RIPEMD160> são considerados fracos.

 Esses algoritmos de criptografia não fornece tanta garantia de segurança como contrapartes mais modernos. Criptografia de algoritmos de hash <xref:System.Security.Cryptography.SHA1> e <xref:System.Security.Cryptography.RIPEMD160> fornecem menor resistência a colisão de algoritmos de hash mais modernos. O algoritmo de criptografia <xref:System.Security.Cryptography.TripleDES> fornece menos bits de segurança que algoritmos de criptografia mais modernos.

## <a name="rule-description"></a>Descrição da Regra
 Algoritmos de criptografia fraca e funções de hash são usadas atualmente para vários motivos, mas não deve ser usados para garantir a confidencialidade dos dados que eles protegem.

 A regra dispara quando ele encontra 3DES, SHA1 ou RIPEMD160 algoritmos no código e gera um aviso ao usuário.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Use as opções de criptografia mais fortes:

-   Para criptografia TripleDES, use <xref:System.Security.Cryptography.Aes> criptografia.

-   Para funções de hash SHA1 ou RIPEMD160, use aquelas no [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) família (por exemplo, <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso dessa regra quando o nível de proteção necessário para os dados não exige uma garantia de segurança.

## <a name="pseudo-code-example"></a>Exemplo de código pseudo
 A partir do momento da redação deste artigo, o exemplo de pseudocódigo a seguir ilustra o padrão detectado por essa regra.

### <a name="sha-1-hashing-violation"></a>Violação de hash SHA-1

```
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();

```

### <a name="solution"></a>Solução

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="ripemd160-br-br-hashing-violation"></a>RIPEMD160 <br /><br />Violação de hash

```
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();

```

### <a name="solution"></a>Solução

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="tripledes-encryption-violation"></a>Violação de criptografia TripleDES

```
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

### <a name="solution"></a>Solução

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```