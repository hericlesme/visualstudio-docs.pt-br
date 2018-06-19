---
title: Propriedades de funções de domínio
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 48e2ba4180e72b68838e33f099fbb31186006698
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31951210"
---
# <a name="properties-of-domain-roles"></a>Propriedades de funções de domínio
As propriedades na tabela a seguir estão associadas com uma função de domínio. Para obter informações sobre as funções de domínio, consulte [compreensão de modelos, Classes e relacionamentos](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriedade|Descrição|Padrão|
|--------------|-----------------|-------------|
|Tipo de coleção|Se essa função possui multiplicidade 0.. * ou 1... \*, essa propriedade personaliza o tipo genérico que é usado para armazenar a coleção de links.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> é usado|
|Atributos personalizados|Atributos que você especificar aqui serão adicionados como atributos para a classe do código gerado.|< nenhum\>|
|Propriedade é pesquisável|Se `True`, e se a multiplicidade da relação for entre 0 e 1 ou 1..1, a propriedade de função pode ser visitada pelo usuário no **propriedades** janela. A propriedade exibe o nome do elemento no final do link de relação.|`True`|
|É o gerador de propriedade|Se `True`, uma propriedade de função é gerada para essa função, que você pode usar para percorrer a relação no código do programa. Se você definir false, você pode percorrer a relação de uma maneira menos eficiente usando métodos estáticos da relação de domínio.|`True`|
|Modificador de acesso de Getter de propriedade|O modificador de acesso para o getter da propriedade gerado (`public`, `internal`, `private`, `protected`, ou `protected internal`).|`public`|
|Modificador de acesso do Setter de propriedade|O modificador de acesso para o setter da propriedade gerado (`public`, `internal`, `private`, `protected`, ou `protected internal`).|`public`|
|Multiplicidade|O número de elementos de modelo que pode executar a função oposta (`0..1`, `1..1`, `0..*`, ou `1..*`). Se a multiplicidade for `0..*` ou `1..*`, em seguida, a propriedade gerada representa uma coleção; caso contrário, a propriedade gerada representa um elemento de modelo único.|Depende do tipo de relação e se essa é a função de origem ou destino na relação.|
|Nome|O nome da função de domínio. Essa propriedade não pode conter espaço em branco.|O nome da classe de domínio do player de função para esta função.|
|Propaga a cópia|`DoNotPropagateCopy` -O executor da função copiado não terá nenhuma cópia deste link.<br /><br /> `PropagateCopyToLinkOnly` -O copiado aponta para existente oposto.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -O copiado aponta para uma cópia do oposto.|`PropagateCopyToLinkAndOppositeRolePlayer` para as funções de origem dos objetos incorporados.<br /><br /> `DoNotPropagateCopy` para outras funções.<br /><br /> Para obter mais informações, consulte [Personalizando comportamento de cópia](../modeling/customizing-copy-behavior.md)|
|Propaga a exclusão|`True` Para excluir o elemento que executa essa função quando o link associado será excluído.|`True` para o destino de uma função incorporada.<br /><br /> `False` para outras funções.<br /><br /> Para obter mais informações, consulte [personalizar o comportamento de exclusão](../modeling/customizing-deletion-behavior.md).|
|Nome da Propriedade|O nome da propriedade gerada no código do player de função. Esse nome não pode conter espaço em branco.|O nome da função oposto se essa função tem um zero-para-um ou uma-para-um multiplicidade; Caso contrário, o nome pluralized da função oposto.|
|Player de função|A classe de domínio do elemento que pode executar essa função na relação. Esta propriedade é somente para leitura.|A classe de domínio do player de função para esta função.|
|Observações|Anotações informais que estão associadas com a função de domínio.|< nenhum\>|
|Categoria|A categoria na qual a propriedade gerada aparece no **propriedades** janela no designer de gerado. Se esta propriedade estiver vazia, a propriedade gerada aparece sob o **Misc** categoria|< nenhum\>|
|Descrição|A descrição que é usada para documentar código e é usada na interface de usuário do designer gerado.<br /><br /> A descrição aparece na dica de ferramenta IntelliSense para a propriedade gerada na classe de player de função.|`Description for` *o nome completo da função*|
|Nome de Exibição|O nome que é exibido no designer gerado para a função de domínio.|O valor ajustado da propriedade Name.|
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a Ajuda de F1 para a função de domínio.|\<Nenhum >|
|Nome de exibição da propriedade|O nome que é exibido no designer gerado para a propriedade de função gerado.|O valor ajustado da propriedade de nome de propriedade.|

> [!NOTE]
> O valor padrão de um nome para exibição é com base no valor da propriedade associada inserindo espaços antes de cada caractere em letra maiuscula que é precedido por um caractere em minúscula e que não é seguido por outro caractere maiusculo.

## <a name="see-also"></a>Consulte também

- [Propriedades de relacionamentos de domínios](../modeling/properties-of-domain-relationships.md)