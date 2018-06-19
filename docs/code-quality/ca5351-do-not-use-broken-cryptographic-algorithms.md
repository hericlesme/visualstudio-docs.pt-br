---
title: CA5351 Não usam algoritmos de criptografia desfeitos
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3aa720459fff6cc67080fd3368cda6ed3a82bfda
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920412"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 Não usam algoritmos de criptografia desfeitos
|||
|-|-|
|NomeDoTipo|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Categoria|Microsoft.Cryptography|
|Alteração Significativa|Não separáveis|

> [!NOTE]
>  Esse aviso última atualização de novembro de 2015.

## <a name="cause"></a>Causa
 Funções de hash como <xref:System.Security.Cryptography.MD5> e algoritmos de criptografia, como <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.RC2> pode expor o risco significativo e pode resultar na exposição de informações confidenciais por meio de técnicas de ataque trivial, como ataques de força bruta e colisões de hash.

 A lista de algoritmos criptográficos abaixo estão sujeitos a ataques de criptografia conhecidos. O algoritmo de hash criptográfico <xref:System.Security.Cryptography.MD5> está sujeita a ataques de colisão de hash.  Dependendo do uso, uma colisão de hash pode levar a representação, violação ou outros tipos de ataques em sistemas que contam com a saída de criptografia exclusiva de uma função de hash. Os algoritmos de criptografia <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.RC2> estão sujeitos a ataques de criptografia que pode resultar na divulgação não intencional de dados criptografados.

## <a name="rule-description"></a>Descrição da Regra
 Dividido criptográfico algoritmos não são considerados seguros e seu uso não é recomendável. O algoritmo de hash MD5 é suscetível a ataques de colisão conhecidos, embora a vulnerabilidade específica irão variar com base no contexto de uso.  Algoritmos de hash usados para garantir a integridade de dados (por exemplo, a assinatura do arquivo ou o certificado digital) estão especialmente vulneráveis.  Nesse contexto, os invasores podem gerar duas partes separadas dos dados, que dados benignos podem ser substituídos com dados mal-intencionados, sem alterar o valor de hash ou anulação de uma assinatura digital associada.

 Algoritmos de criptografia:

-   <xref:System.Security.Cryptography.DES> criptografia contém um tamanho de chave pequenas, que pode ser forçado bruta em menos de um dia.

-   <xref:System.Security.Cryptography.RC2> a criptografia é suscetível a um ataque de chave relacionados, em que o invasor localiza matemáticas relações entre todos os valores de chave.

 Essa regra dispara quando ele encontra qualquer uma das funções criptográficas acima no código-fonte e gera um aviso ao usuário.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Use as opções de criptografia mais fortes:

-   Para MD5, use hashes no [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) família (por exemplo, <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

-   Para DES e RC2, use <xref:System.Security.Cryptography.Aes> criptografia.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso dessa regra, a menos que é revisada por um especialista de criptografia.

## <a name="pseudo-code-example"></a>Exemplo de código pseudo
 O exemplo de pseudocódigo a seguir ilustra o padrão detectado por essa regra e uma das alternativas.

### <a name="md5-hashing-violation"></a>MD5 Violação de hash

```
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();

```

### <a name="solution"></a>Solução

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="rc2-encryption-violation"></a>RC2 Violação de criptografia

```
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();

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

### <a name="des-br-br-encryption-violation"></a>DES <br /><br />Violação de criptografia

```
using System.Security.Cryptography;
...
DES encAlg = DES.Create();

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