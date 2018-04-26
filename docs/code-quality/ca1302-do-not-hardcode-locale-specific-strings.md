---
title: 'CA1302: não codificar cadeias de caracteres específicas da localidade'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a00f78739a9287c996e87f182ca34ecba6d484c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: não codificar cadeias de caracteres específicas da localidade
|||
|-|-|
|NomeDoTipo|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um método usa uma cadeia de caracteres literal que representa a parte do caminho de determinadas pastas do sistema.

## <a name="rule-description"></a>Descrição da Regra
 O <xref:System.Environment.SpecialFolder?displayProperty=fullName> enumeração contém membros que se referem a pastas do sistema especial. Os locais das pastas podem ter valores diferentes em diferentes sistemas operacionais, o usuário pode alterar alguns dos locais e os locais são localizados. Um exemplo de uma pasta especial é a pasta do sistema, que é "C:\WINDOWS\system32" em [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] mas "C:\WINNT\system32" em [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. O <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> método retorna os locais que estão associados a <xref:System.Environment.SpecialFolder> enumeração. Os locais que são retornados pelo <xref:System.Environment.GetFolderPath%2A> estão localizados e apropriado para o computador em execução no momento.

 Essa regra cria tokens de caminhos de pastas que são recuperados por meio de <xref:System.Environment.GetFolderPath%2A> método em níveis de diretório separado. Cada cadeia de caracteres literal é comparada com os tokens. Se uma correspondência for encontrada, presume-se que o método é criar uma cadeia de caracteres que refere-se para o local do sistema que está associado com o token. Para a portabilidade e localização, use o <xref:System.Environment.GetFolderPath%2A> método para recuperar os locais das pastas do sistema especiais em vez de usar literais de cadeia de caracteres.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, recuperar o local usando o <xref:System.Environment.GetFolderPath%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso de que essa regra se a cadeia de caracteres literal não é usada para se referir a um dos locais do sistema que está associado com o <xref:System.Environment.SpecialFolder> enumeração.

## <a name="example"></a>Exemplo
 O exemplo a seguir cria o caminho da pasta de dados do aplicativo comum, que gera três avisos dessa regra. Em seguida, o exemplo recupera o caminho usando o <xref:System.Environment.GetFolderPath%2A> método.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1303: não passar literais como parâmetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)