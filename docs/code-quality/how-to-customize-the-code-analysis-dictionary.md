---
title: "Como: personalizar o dicionário de análise de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7fa5f88a3578998fca325500a3815b909b6ce4a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Como personalizar o dicionário de análise do código
Análise de código usa um dicionário interno para verificar identificadores em seu código para erros de ortografia, caso gramatical e outras convenções de nomenclatura do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] diretrizes. Você pode criar um arquivo Xml de dicionário personalizado para adicionar, remover ou modificar os termos e abreviações acrônimos ao dicionário interno.  
  
 Por exemplo, suponha que seu código continha uma classe denominada **DoorKnokker**. Análise de código deve identificar o nome como um composto de duas palavras: **porta** e **knokker**. Em seguida, ele seria gerar um aviso que **knokker** não foi digitado corretamente. Para forçar a análise de código para reconhecer a ortografia, você pode adicionar o termo **knokker** ao dicionário personalizado.  
  
## <a name="to-create-a-custom-dictionary"></a>Para criar um dicionário personalizado  
 Criar um arquivo chamado **CustomDictionary.xml**.  
  
 Define as palavras personalizadas usando a seguinte estrutura XML:  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>knokker</Word>  
         </Unrecognized>  
         <Recognized>  
            <Word></Word>  
         </Recognized>  
         <Deprecated>  
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
         </Compound>  
         <DiscreteExceptions>  
            <Term></Term>  
         </DiscreteExceptions>  
      </Words>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym></Acronym>  
         </CasingExceptions>  
      </Acronyms>  
   </Dictionary>  
```  
  
## <a name="custom-dictionary-elements"></a>Elementos do dicionário personalizado  
 Você pode modificar o comportamento do dicionário de análise de código, adicionando termos como o texto interno dos seguintes elementos no dicionário personalizado:  
  
-   [Dicionário/palavras/reconhecido/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [Dicionário/palavras/não reconhecida/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [Dicionário/palavras/preterido/termo [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [Dicionário/palavras/compostas/termo [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [Dicionário/palavras/DiscreteExceptions/termo](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [Dicionário/acrônimos/CasingExceptions/acrônimo](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a>Dicionário/palavras/reconhecido/Word  
 Para incluir um termo na lista de termos que identifica de análise de código como escrito corretamente, adicione o termo como o texto interno de um elemento/palavras/reconhecido/palavra do dicionário. Termos de elementos do dicionário/palavras/reconhecido/Word não diferenciam maiusculas de minúsculas.  
  
 **Exemplo**  
  
```  
<Dictionary>  
      <Words>  
         <Recognized>  
            <Word>knokker</Word>  
            ...  
         </Recognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Termos de palavras/dicionário/reconhecido nós são aplicados para as regras de análise de código a seguir:  
  
-   [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: os literais devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>Dicionário/palavras/não reconhecida/Word  
 Para excluir uma condição na lista de termos que identifica de análise de código como escrito corretamente, adicione o termo a ser excluído como o texto interno de um elemento/palavras/não reconhecida/palavra do dicionário. Termos de elementos do dicionário/palavras/não reconhecida/Word não diferenciam maiusculas de minúsculas.  
  
 **Exemplo**  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>meth</Word>  
            ...  
         </Unrecognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Termos do nó de dicionário/palavras/não reconhecida são aplicados para as regras de análise de código a seguir:  
  
-   [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: os literais devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>Dicionário/palavras/preterido/termo [@PreferredAlternate]  
 Para incluir um termo na lista de termos que identifica de análise de código como preteridos, adicione o termo como o texto interno de um elemento de dicionário/palavras/preterido/termo. Um termo reprovado é uma palavra que está escrita corretamente, mas não deve ser usada.  
  
 Para incluir um termo alternativo sugerido no aviso, especifique a alternativa no atributo PreferredAlternate do elemento de termo. Você pode deixar o valor do atributo vazio se você não deseja sugerir uma alternativa.  
  
-   O termo reprovado no dicionário / / elemento obsoleto/termo não diferencia maiusculas de minúsculas.  
  
-   O valor do atributo PreferredAlternate diferencia maiusculas de minúsculas. Use Pascal case para alternativas compostas.  
  
 **Exemplo**  
  
```  
<Dictionary>  
      <Words>  
         <Deprecated>  
            <Term PreferredAlternate="LogOn">login</Term>  
            ...  
         </Deprecated>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Termos do nó de palavras/dicionário/preterido são aplicados para as regras de análise de código a seguir:  
  
-   [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>Dicionário/palavras/compostas/termo [@CompoundAlternate]  
 O dicionário interno identifica alguns termos como termos simples e discretos, em vez de um termo composto. Para incluir um termo na lista de termos que identifica a análise de código como uma palavra composta e especifique a caixa correta do termo, adicione o termo como o texto interno de um elemento de dicionário/palavras/compostas/termo. No atributo CompoundAlternate do elemento de termo, especifique as palavras individuais que compõem o termo composto colocando em maiuscula a primeira letra das palavras individuais (caso Pascal). Observe que o termo especificado no texto interno é automaticamente adicionado à lista de palavras/dicionário/DiscreteExceptions.  
  
-   O termo reprovado no dicionário / / elemento obsoleto/termo não diferencia maiusculas de minúsculas.  
  
-   O valor do atributo PreferredAlternate diferencia maiusculas de minúsculas. Use Pascal case para alternativas compostas.  
  
 **Exemplo**  
  
```  
<Dictionary>  
      <Words>  
         <Compound>  
            <Term CompoundAlternate="CheckBox">checkbox</Term>  
            ...  
         </Compound>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Termos do nó de palavras/dicionário/compostas são aplicados para as regras de análise de código a seguir:  
  
-   [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>Dicionário/palavras/DiscreteExceptions/termo  
 Para excluir um termo na lista de termos que identifica a análise de código como um único, o word discreto quando o termo estiver marcado, as regras de maiusculas e minúsculas para palavras compostas, adicionar o termo como o texto interno de um elemento de dicionário/palavras/DiscreteExceptions/termo. O termo no elemento do dicionário/palavras/DiscreteExceptions/termo não diferencia maiusculas de minúsculas.  
  
 **Exemplo**  
  
```  
<Dictionary>  
      <Words>  
         <DiscreteExceptions>  
            <Term>checkbox</Term>  
            ...  
         </DiscreteExceptions>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Termos do nó de palavras/dicionário/DiscreteExceptions são aplicados para as regras de análise de código a seguir:  
  
-   [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>Dicionário/acrônimos/CasingExceptions/acrônimo  
 Para incluir um acrônimo na lista de termos que identifica a análise de código como digitada corretamente e para indicar como o acrônimo quando o termo estiver marcado, o uso de maiusculas e minúsculas as regras para palavras compostas, adicionar o termo como o texto interno de um dicionário/acrônimos/CasingExceptions / Elemento ACRONYM. O acrônimo no elemento do dicionário/acrônimos/CasingExceptions/acrônimo diferencia maiusculas de minúsculas.  
  
 **Exemplo**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 Termos no nó acrônimos/dicionário/CasingExceptions são aplicados para as regras de análise de código a seguir:  
  
-   [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>Para aplicar um dicionário personalizado a um projeto  
  
1.  Em **Solution Explorer**, use um dos procedimentos a seguir:  
  
2.  Para adicionar um dicionário para um único projeto, clique no nome do projeto e, em seguida, clique em **Add Existing Item**. Especifique o arquivo de **Add Existing Item** caixa de diálogo.  
  
3.  Para adicionar um dicionário que é compartilhado entre dois ou mais projetos, localize o arquivo para compartilhar o **Add Existing Item** caixa de diálogo, clique na seta para baixo no **adicionar** botão e, em seguida, clique em **adicionar como vínculo** .  
  
4.  Em **Solution Explorer**, com o botão direito do **CustomDictionary.xml** nome de arquivo e clique em **propriedades**.  
  
5.  Do **ação de compilação** lista, selecione **CodeAnalysisDictionary**.  
  
6.  Do **copiar para diretório de saída** lista, selecione **não copiar**.