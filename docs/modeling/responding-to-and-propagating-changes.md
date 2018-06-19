---
title: Respondendo a alterações e propagando-as
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d87a93016f2004a45a572374d68a20d2e59073da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953999"
---
# <a name="responding-to-and-propagating-changes"></a>Respondendo a alterações e propagando-as
Quando um elemento é criado, excluído ou atualizado, você pode escrever código que se propaga a alteração para outras partes do modelo, ou para recursos externos como arquivos, bancos de dados ou outros componentes.

## <a name="in-this-section"></a>Nesta seção
 Como diretriz, considere estas técnicas na seguinte ordem:

|Técnica|Cenários|Para obter mais informações|
|---------------|---------------|--------------------------|
|Defina uma propriedade de domínio calculado.|Uma propriedade de domínio cujo valor é calculado a partir de outras propriedades no modelo. Por exemplo, um preço que é a soma dos preços de elementos relacionados.|[Propriedades calculadas e de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Defina uma propriedade de domínio de armazenamento personalizado.|Uma propriedade de domínio armazenada em outras partes do modelo ou externamente. Por exemplo, você pode analisar uma cadeia de caracteres de expressão em uma árvore no modelo.|[Propriedades calculadas e de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Substituir os manipuladores de alteração como OnValueChanging e OnDeleting|Mantenha diferentes elementos em sincronia e valores externos em sincronia com o modelo.<br /><br /> Restringir os valores em intervalos definidos.<br /><br /> Chamado imediatamente antes e após o valor da propriedade e outras alterações. Você pode encerrar a alteração lançando uma exceção.|[Manipuladores de alterações nos valores da propriedade de domínio](../modeling/domain-property-value-change-handlers.md)|
|Regras|Você pode definir regras que estão enfileiradas para execução apenas antes do final de uma transação em que uma alteração tiver ocorrido. Eles não são executados em Desfazer ou refazer. Usá-los para manter uma parte do armazenamento em sincronia com o outro.|[Regras propagam alterações dentro do modelo](../modeling/rules-propagate-changes-within-the-model.md)|
|Eventos de armazenamento|O repositório de modelagem fornece notificações de eventos, como adicionar ou excluir um elemento ou um link ou alterando o valor de uma propriedade. O evento também é executado em Desfazer e refazer. Use eventos de armazenamento para atualizar os valores que não estão no repositório.|[Manipuladores de eventos propagam alterações fora do modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Eventos do .NET|Formas com manipuladores de eventos que respondem a cliques do mouse e outros gestos. Você deve registrar esses eventos para cada objeto. Registro normalmente é feito em uma substituição de InitializeInstanceResources e deve ser feito para cada elemento.<br /><br /> Normalmente, esses eventos ocorrem fora de uma transação.|[Como interceptar um clique em uma forma ou um decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Regras de limites|Uma regra de limite é usada especificamente para restringir os limites de uma forma.|[BoundsRules restringem o local e o tamanho de uma forma](../modeling/boundsrules-constrain-shape-location-and-size.md)|
|Regras de seleção|Regras de seleção restringem especificamente o que o usuário pode selecionar.|[Como acessar e restringir a seleção atual](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Indica estados dos elementos de modelo usando os recursos de formas e conectores como sombra, pontas de seta, cor e larguras de linha e estilo.|[Atualizando formas e conectores para refletir o modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="comparing-rules-and-store-events"></a>**Comparando as regras e os eventos de armazenamento**
 Alterar notifiers, regras e eventos são executados quando ocorrerem alterações em um modelo.

 Geralmente, as regras são aplicadas na transação final na qual a alteração ocorreu e eventos são aplicados depois que as alterações em uma transação são confirmadas.

 Use armazenamento de eventos para sincronizar o modelo com objetos fora do repositório e regras para manter a consistência no repositório de.

-   **Criação de regras personalizadas** você criar uma regra personalizada como uma classe derivada de uma regra abstrata. Você também deve notificar a estrutura sobre a regra personalizada. Para obter mais informações, consulte [regras propagar as alterações no modelo de](../modeling/rules-propagate-changes-within-the-model.md).

-   **Assinando eventos** antes de assinar um evento, crie um manipulador de eventos e representante. Em seguida, use o <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>propriedade para assinar o evento. Para obter mais informações, consulte [manipuladores de propagar alterações fora do modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).

-   **Desfazendo alterações** ao desfazer uma transação, os eventos são gerados, mas as regras não são aplicadas. Se um valor de alterações de uma regra e desfaça a alteração, o valor será redefinido para o valor original durante a ação de desfazer. Quando um evento é gerado, você deve alterar manualmente o valor para o seu valor original. Para saber mais sobre transactons e desfazer, consulte [como: usar transações para atualizar o modelo](../modeling/how-to-use-transactions-to-update-the-model.md).

-   **Passando argumentos de eventos para eventos e regras** ambos os eventos e as regras são transmitidas uma `EventArgs` parâmetro que tem informações sobre como o modelo foi alterado.

## <a name="see-also"></a>Consulte também

- [Como interceptar um clique em uma forma ou um decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Escrevendo código para personalizar uma linguagem específica de domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)