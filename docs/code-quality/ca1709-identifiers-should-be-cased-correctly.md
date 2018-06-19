---
title: 'CA1709: os identificadores do recurso devem ter maiúsculas e minúsculas corretas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 589ef84b5291b9e674d5d540b75edd5e7f8edbaf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915636"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: os identificadores do recurso devem ter maiúsculas e minúsculas corretas
|||
|-|-|
|NomeDoTipo|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra - quando gerado em assemblies, namespaces, tipos, membros e parâmetros.<br /><br /> Não quebra - quando disparado em parâmetros de tipo genérico.|

## <a name="cause"></a>Causa
 O nome de um identificador não é maiusculas e minúsculas corretas.

 \- ou -

 O nome de um identificador contém um acrônimo de duas letras e a segunda letra é minúscula.

 \- ou -

 O nome de um identificador contém um acrônimo de três ou mais letras maiusculas.

## <a name="rule-description"></a>Descrição da Regra
 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.

 Por convenção, os nomes de parâmetro usam concatenação com maiusculas e minúsculas; nomes de namespace, tipo e membro usar Pascal maiusculas e minúsculas. Um nome concatenados, a primeira letra é minúscula e a primeira letra de qualquer palavras restantes no nome está em letras maiusculas. Exemplos de nomes concatenados são "packetSniffer", "ioFile" e "fatalErrorCode". Em um nome de maiusculas e minúsculas de Pascal, a primeira letra é maiuscula e a primeira letra de qualquer palavras restantes no nome está em letras maiusculas. Exemplos de nomes de maiusculas e minúsculas de Pascal são "PacketSniffer", "IOFile" e "FatalErrorCode".

 Essa regra divide o nome em palavras com base em maiusculas e minúsculas e verifica as palavras de duas letras em relação a uma lista de palavras comuns de duas letras, como "In" ou "My". Se uma correspondência não for encontrada, a palavra é considerada um acrônimo. Além disso, essa regra pressupõe encontrou um acrônimo quando o nome contém quatro letras maiusculas em uma linha ou três letras maiusculas em uma linha no final do nome.

 Por convenção, siglas de duas letras usam todas as letras maiusculas e acrônimos de três ou mais caracteres Pascal maiusculas e minúsculas. Os exemplos a seguir usam essa convenção de nomenclatura: 'DB', 'CR', 'Contador' e 'Ecma'. Os exemplos a seguir violam a convenção: 'i /', 'XML' e 'DoD' e para nomes de nonparameter, 'xp' e 'Painel de controle'.

 'ID' é especial de maiusculas e minúsculas para fazer com que uma violação desta regra. 'Id' não é um acrônimo, mas é uma abreviação para 'identificação'.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Altere o nome para que ele é maiusculas e minúsculas corretas.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir este aviso se você tem suas próprias convenções de nomenclatura, ou se o identificador representa um nome apropriado, por exemplo, o nome de uma empresa ou uma tecnologia.

 Você também pode adicionar termos específicos, abreviações e acrônimos que para um dicionário personalizado de análise de código. Termos especificados no dicionário personalizado não irá causar violações desta regra. Para obter mais informações, consulte [como: personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Regras relacionadas
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)