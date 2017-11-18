---
title: 'CA1704: Os identificadores devem ser grafados corretamente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e43e3340cdbc05ec00c909542e201692199ccfef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: os identificadores do recurso devem ter a ortografia correta
|||  
|-|-|  
|NomeDoTipo|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 O nome de um identificador contém uma ou mais palavras que não são reconhecidas pela biblioteca do verificador ortográfico do Microsoft. Esta regra não Verifique construtores ou membros denominado especial, como get e definir acessadores de propriedade.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra analisa o identificador em tokens e verifica a ortografia de cada token. O algoritmo de análise executa as transformações a seguir:  
  
-   Letras maiusculas iniciar um novo token. Por exemplo, MyNameIsJoe cria tokens "Meu", "Name", "É", "Joe".  
  
-   Para várias letras maiusculas, a última letra maiuscula inicia um novo token. Por exemplo, GUIEditor cria tokens para "GUI", "Editor".  
  
-   À esquerda e à direita apóstrofos são removidos. Por exemplo, 'remetente' cria tokens para "sender".  
  
-   Sublinhados significam o final de um token em são removidos. Por exemplo, Hello_world cria tokens para "Hello", "world".  
  
-   E comercial inseridos é removidos. Por exemplo, para & mat cria tokens para "Formatar".  
  
 Por padrão, a versão em inglês (en) do verificador ortográfico é usada. Não há outros dicionários de idiomas estão disponíveis no momento.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, corrija a ortografia da palavra ou adicionar a palavra ao dicionário personalizado chamado CustomDictionary.xml. Coloque o dicionário no diretório de instalação da ferramenta, o diretório do projeto, ou no diretório que está associado com a ferramenta de perfil do usuário (%USERPROFILE%\Application\\...). Para aprender a adicionar dicionário personalizado a um projeto em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consulte [como: personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
-   Adicione palavras que não devem causar uma violação no caminho palavras/dicionário/reconhecido.  
  
-   Adicione palavras que poderiam causar uma violação no caminho de dicionário/palavras/não reconhecida.  
  
-   Adicione palavras que devem ser sinalizadas como obsoletos no caminho palavras/dicionário/preterido. Consulte o tópico relacionado regra [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md) para obter mais informações.  
  
-   Adicione exceções às regras de maiusculas e minúsculas acrônimo para o caminho de acrônimos/dicionário/CasingExceptions.  
  
 Este é um exemplo da estrutura de um arquivo de dicionário personalizado.  
  
```  
<Dictionary>  
   <Words>  
      <Unrecognized>  
         <Word>cb</Word>  
      </Unrecognized>  
      <Recognized>  
         <Word>stylesheet</Word>  
         <Word>GotDotNet</Word>  
      </Recognized>  
      <Deprecated>  
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>  
      </Deprecated>  
   </Words>  
   <Acronyms>  
      <CasingExceptions>  
         <Acronym>CJK</Acronym>  
         <Acronym>Pi</Acronym>  
      </CasingExceptions>  
   </Acronyms>  
</Dictionary>  
```  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso dessa regra somente se a palavra é intencionalmente incorreta e o word aplica-se a um conjunto limitado de biblioteca. Corretamente palavras reduzem a curva de aprendizado que é necessária para novas bibliotecas de software.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2204: os literais devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)  
  
## <a name="see-also"></a>Consulte também  
 [Como personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
