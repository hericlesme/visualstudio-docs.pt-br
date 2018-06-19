---
title: Personalizando e estendendo uma linguagem específica do domínio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e6a6bb74d4b4a4fc93c4cf0425c1fe06b9f290a4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953369"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personalizando e estendendo uma linguagem específica do domínio
O Visual Studio de modelagem e visualização SDK (VMSDK) fornece vários níveis em que você pode definir as ferramentas de modelagem:

1.  Defina uma linguagem específica de domínio (DSL) utilizando o diagrama de definição de DSL. Você pode criar rapidamente uma DSL com uma notação diagramática, um formato XML legível e as ferramentas básicas que são necessárias para gerar o código e outros artefatos.

     Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md).

2.  Ajuste o DSL usando recursos mais avançados da definição de DSL. Por exemplo, você pode fazer com que os links adicionais aparecem quando o usuário cria um elemento. Essas técnicas são obtidas principalmente na definição de DSL e alguns exigem algumas linhas de código do programa.

3.  Estenda suas ferramentas de modelagem usando o código do programa. O VMSDK foi projetado especificamente para facilitar a integração de suas extensões com o código gerado a partir da Definição de DSL.  Para obter mais informações, consulte [escrevendo código para personalizar uma linguagem específica do domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
>  Quando você atualizou o arquivo de definições de DSL, não se esqueça de clicar em **transformar todos os modelos** na barra de ferramentas do Gerenciador de soluções antes de recompilar a solução.

##  <a name="customShapes"></a> Nesta seção

|Para obter esse efeito|Consulte este tópico|
|----------------------------|-------------------------|
|Permitir que o usuário definir as propriedades de estilo e a cor de uma forma.|A classe do conector ou a forma de atalho, aponte para **adicionar expostos**e clique em um item.<br /><br /> Consulte [personalizando apresentação no diagrama](../modeling/customizing-presentation-on-the-diagram.md).|
|No diagrama, compartilhamento de propriedades como inicial altura e largura, a cor, dicas de ferramenta semelhante diferentes classes de elemento de modelo.|Use a herança entre classes de conector ou formas. Mapeamentos entre as formas derivadas e classes derivadas de domínio herdam os detalhes de mapeamento dos pais.<br /><br /> Ou então, mapear as classes de domínio diferente para a mesma classe de forma.|
|Uma classe de elemento de modelo é exibida por contextos de formas diferentes.|Mais de uma classe de forma são mapeados para a mesma classe de domínio. Quando você compila a solução, execute o relatório de erros e forneça o código solicitado para decidir o que forma a ser usada.|
|Cor da forma ou outros recursos como fonte indicam o estado atual.|Consulte [atualização formas e conectores para refletir o modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Crie uma regra que atualiza as propriedades expostas. Consulte [regras propagam as alterações no modelo](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Ou então, usar OnAssociatedPropertyChanged() para atualizar recursos não expostos como setas de link ou fonte.|
|Ícone de alterações de forma para indicar o estado.|Defina a visibilidade do decorador mapeamento na janela de detalhes de DSL. Localize vários decoradores de imagem na mesma posição. Consulte [atualização formas e conectores para refletir o modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Ou, substitua `ImageField.GetDisplayImage()`. Consulte o exemplo <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|
|Definir uma imagem de plano de fundo de qualquer forma|Substitua InitializeInstanceResources() para adicionar um ImageField ancorada. Consulte [personalizando apresentação no diagrama](../modeling/customizing-presentation-on-the-diagram.md).|
|Formas de aninhamento para qualquer profundidade|Configure a inserção de árvore recursiva. Defina BoundsRules para conter as formas. Consulte [personalizando apresentação no diagrama](../modeling/customizing-presentation-on-the-diagram.md).|
|Anexe conectores momentos fixa no limite de um elemento.|Defina elementos terminal incorporados, representados por portas pequenas no diagrama. Use BoundsRules para corrigir as portas em vigor. Consulte o exemplo de diagrama de circuito em [visualização e modelagem SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|
|Campo de texto exibe um valor derivado de outros valores.|Mapear o decorador de texto para uma propriedade de domínio calculado ou armazenamento personalizado. Para obter mais informações, consulte [calculado e as propriedades de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md).|
|Propagar alterações entre elementos de modelo, ou entre formas|Consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).|
|Propagar alterações de recursos, como outros [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões fora da loja.|Consulte [manipuladores de eventos propagam alterações fora do modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Janela Propriedades exibe as propriedades de um elemento relacionado.|Configure o encaminhamento de propriedade. Consulte [personalizar a janela de propriedades](../modeling/customizing-the-properties-window.md).|
|Categorias de propriedades|A janela Propriedades é dividida em seções denominadas categorias. Definir o **categoria** de seu domínio. Propriedades com o mesmo nome de categoria serão exibida na mesma seção. Você também pode definir o **categoria** de uma função de relação.|
|Controlar o acesso do usuário para propriedades de domínio|Definir **é navegável** false para impedir que uma propriedade de domínio que aparecem na janela Propriedades em tempo de execução. Você ainda pode mapeá-lo para decoradores de texto.<br /><br /> **Interface de usuário somente leitura** impede que os usuários alterem uma propriedade de domínio.<br /><br /> Acesso de programa para a propriedade de domínio não é afetado.|
|Altere o nome, o ícone e a visibilidade de nós no Gerenciador de modelos do DSL.|Consulte [Personalizando o Gerenciador de modelos](../modeling/customizing-the-model-explorer.md).|
|Habilitar copiar, recortar e colar|Definir o **habilitar copiar-colar** propriedade o **Editor** nó no Gerenciador de DSL.|
|Links de referência de cópia e suas metas sempre que um elemento é copiado. Por exemplo, copie comentários anexados a um item.|Definir o **cópia propaga** propriedade da função de origem (representada pela linha em um lado da relação de domínio no diagrama de definição de DSL).<br /><br /> Escreva código para substituir ProcessOnCopy para obter efeitos mais complexos.<br /><br /> Consulte [personalizar o comportamento de cópia](../modeling/customizing-copy-behavior.md).|
|Excluir, reassociar ou vincular novamente os elementos relacionados quando um elemento é excluído.|Definir o **propaga excluir** valor de uma função de relação. Efeitos mais complexos, substituir `ShouldVisitRelationship` e `ShouldVisitRolePlayer` métodos o `MyDslDeleteClosure` definido na classe **DomainModel.cs**<br /><br /> Consulte [personalizar o comportamento de exclusão](../modeling/customizing-deletion-behavior.md)|
|Preserve o layout de forma e a aparência na cópia e arraste e solte.|Adicionar as formas e os conectores para copiado `ElementGroupPrototype`. É o método mais conveniente para substituir `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Consulte [personalizar o comportamento de cópia](../modeling/customizing-copy-behavior.md).|
|Cole formas em um local escolhido, como a posição atual do cursor.|Substituir `ClipboardCommandSet.ProcessOnCopy()` para usar a versão específica do local de `ElementOperations.Merge().` consulte [Personalizando comportamento de cópia](../modeling/customizing-copy-behavior.md).|
|Criar links adicionais ao colar|Override ClipboardCommandSet.ProcessOnPasteCommand()|
|Habilitar arrastar e soltar neste diagrama, outras DSLs e Windows elementos|Consulte [como: adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Permitir que uma ferramenta para ser arrastado para uma forma de filho, como uma porta ou a forma como se ele foi arrastado para o pai.|Defina uma política de mesclagem Element na classe de objeto de destino para encaminhar o objeto removido para o pai. Consulte [Personalizando a criação de elemento e a movimentação de](../modeling/customizing-element-creation-and-movement.md).|
|Permitir que uma forma ou a ferramenta a ser arrastado para uma forma e têm links adicionais ou objetos criados. Por exemplo, para permitir um comentário a ser descartado em um item para o qual é a ser vinculado.|Definir uma política de mesclagem Element na classe de domínio de destino e definir os links a serem gerados. Em casos complexos, você pode adicionar código personalizado. Consulte [Personalizando a criação de elemento e a movimentação de](../modeling/customizing-element-creation-and-movement.md).|
|Crie um grupo de elementos com uma ferramenta. Por exemplo, um componente com um conjunto fixo de portas.|Substitua o método de inicialização da caixa de ferramentas no ToolboxHelper.cs. Crie um protótipo de grupo de elemento (EGP) que contém os elementos e seus vínculos de relação. Consulte [personalizando ferramentas e a caixa de ferramentas](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Inclua as formas de principais e a porta em que o EGP ou definir BoundsRules para posicionar as formas de porta quando o EGP é instanciado. Consulte [BoundsRules restringir o local de forma e tamanho](../modeling/boundsrules-constrain-shape-location-and-size.md).|
|Use uma ferramenta de conexão para criar uma instância de vários tipos de relação.|Adicione Link conectar diretivas (LCD) para o construtor de Conexão que é invocado pela ferramenta. Os LCDs determinam o tipo de relação entre os tipos de dois elementos. Para fazer isso dependem dos estados dos elementos, você pode adicionar código personalizado. Consulte [personalizando ferramentas e a caixa de ferramentas](../modeling/customizing-tools-and-the-toolbox.md).|
|Ferramentas aderência - o usuário pode clicar duas vezes qualquer ferramenta para criar vários conectores ou formas em sucessão.|No Explorador de DSL, selecione o `Editor` nó. Na janela Propriedades, defina **usa Autoadesivas itens da caixa de ferramentas**.|
|Definir os comandos de menu|Consulte [como: modificar um comando de Menu padrão](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Restringir o modelo com as regras de validação|Consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md)|
|Gere código, arquivos de configuração ou documentos de uma DSL.|[Gerando código com base em uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Personalizar como os modelos são salvos em arquivo.|Consulte [Personalizando a serialização de XML e armazenamento de arquivos](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Salve modelos de bancos de dados ou outra mídia.|Substituir *YourLanguage*DocData<br /><br /> Consulte [Personalizando a serialização de XML e armazenamento de arquivos](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integre vários DSLs para que eles funcionem como parte de um aplicativo.|Consulte [integrar modelos usando o Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Permitir que seu DSL a ser estendido por terceiros e controlar a extensão.|[Estender a DSL usando MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Compartilhando classes entre DSLs por meio de uma biblioteca de DSLs](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definindo uma política de bloqueio para criar segmentos somente leitura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Consulte também

- [Como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md)
- [Escrevendo código para personalizar uma linguagem específica de domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [SDK de Modelagem para Visual Studio – linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]