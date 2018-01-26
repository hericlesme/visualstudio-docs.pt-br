---
title: "Noções básicas sobre modelos, Classes e relacionamentos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b6e23b91f411cd5260d31927ec35957a3f6c00c1
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="understanding-models-classes-and-relationships"></a>Noções básicas sobre modelos, classes e relações
Uma linguagem específica de domínio (DSL) é definida por seu arquivo de definição de DSL, junto com qualquer código de programa personalizado que você pode escrever. A maioria do código do programa na solução DSL é gerada a partir desse arquivo.  
  
 Este tópico explica os recursos centrais da definição de DSL.  
  
## <a name="the-dsl-definition"></a>A definição de DSL  
 Quando você abre `Dsl\DslDefinition.dsl`, seu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela se parece com a imagem a seguir.  
  
 ![designer de DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 As informações mais importantes na definição de DSL são exibidas no diagrama DSL definição. Informações adicionais, que também é parte do DslDefinition.dsl, são exibidas no Gerenciador de DSL, que geralmente aparece no lado do diagrama. Você trabalha com o diagrama para as tarefas mais frequentes e com o Gerenciador de DSL para personalizações mais avançadas.  
  
 O diagrama de definição de DSL mostra as classes de domínio que definem os elementos de modelo e as relações que definem os links entre os elementos de modelo. Ele também mostra as formas e conectores que são usados para exibir os elementos de modelo para o usuário.  
  
 ![designer de DSL com swimlane](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 Quando você seleciona um item na definição de DSL, no diagrama ou no Gerenciador de DSL, obter informações sobre como ele são exibidas na janela Propriedades. Informações adicionais podem ser exibidas na janela de detalhes de DSL.  
  
### <a name="models-are-instances-of-dsls"></a>Os modelos são instâncias de DSLs  
 Um *modelo* é uma instância de seu DSL criada por um usuário. Um modelo contém elementos de modelo, que são instâncias das classes de domínio que você define e links entre os elementos, que são instâncias das relações de domínio que você definir. Um modelo também pode ter formas e conectores, que exibem os elementos de modelo e links em um diagrama. A definição de DSL inclui as classes de forma, classes do conector e uma classe para o diagrama.  
  
 Uma definição de DSL também é conhecido como um *modelo de domínio*. Um modelo DSL definição ou o domínio é a representação de tempo de design de linguagem específica de domínio, enquanto o modelo é a instanciação de tempo de execução da linguagem específica de domínio.  
  
## <a name="domain-classes-define-model-elements"></a>Classes de domínio definem elementos de modelo  
 Classes de domínio são usados para criar os vários elementos no domínio e relações de domínio são os links entre os elementos. Eles são a representação de tempo de design, os elementos e links que serão instanciados pelos usuários da linguagem de design específicas ao criar seus modelos.  
  
 Esta ilustração mostra um modelo que tenha sido criado pelo usuário de uma biblioteca de música DSL. Álbuns de música são representadas por caixas que contêm listas de músicas. Artistas são representadas por caixas quadrilátero e estão conectadas à álbuns ao qual eles contribuíram.  
  
 ![Modelo de instância de DSL gerado](../modeling/media/music_instance.png "Music_Instance")  
  
 A definição de DSL separa dois aspectos. A aparência dos elementos de modelo no diagrama de modelo é definida usando classes de forma e conector. As informações divulgadas no modelo são definidas usando classes de domínio e as relações de domínio.  
  
 A ilustração a seguir mostra as classes de domínio e as relações na definição de DSL da biblioteca de músicas.  
  
 ![Relações de referência e inserindo](../modeling/media/music_classes.png "Music_Classes")  
  
 A ilustração mostra quatro classes de domínio: música, álbum, artista e música. As classes de domínio definem propriedades do domínio, como nome, título e assim por diante. No modelo de instância, os valores de algumas dessas propriedades são exibidos no diagrama.  
  
 Entre as classes são relações de domínio: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs e ArtistAppearedOnAlbums. As relações tiverem multiplicidades como 1..1, 0.. *. Por exemplo, cada música deve estar relacionada a exatamente uma álbum por meio da relação AlbumHasSongs. Cada álbum pode ter qualquer número de músicas.  
  
### <a name="rearranging-the-dsl-definition-diagram"></a>Reorganizar o diagrama de definição de DSL  
 Observe que uma classe de domínio pode aparecer várias vezes no diagrama de definição de DSL, como o álbum nesta imagem. Sempre há um modo de exibição principal e pode haver alguns *referência* modos de exibição.  
  
 Para reorganizar o diagrama de definição de DSL, você pode:  
  
-   Trocar principal e fazer referência a exibições usando o **coloque aqui árvore** e **divisão árvore** comandos. Clique em uma classe de domínio único para ver esses comandos.  
  
-   Reordene as classes de domínio e forma, pressionando Ctrl + seta para cima e Ctrl + seta para baixo.  
  
-   Recolher ou expandir classes usando o ícone no canto superior direito de cada forma.  
  
-   Recolher partes da árvore clicando no sinal de subtração (-) na parte inferior de uma classe de domínio.  
  
## <a name="inheritance"></a>Herança  
 Classes de domínio podem ser definidas usando a herança. Para criar uma derivação de herança, clique na ferramenta de herança, clique na classe derivada e, em seguida, clique na classe base. Um elemento de modelo tem todas as propriedades que são definidas em sua própria classe de domínio, juntamente com todas as propriedades herdadas da classe base. Ele também herda suas funções em relações.  
  
 Herança também pode ser usada entre relações, formas e conectores. Herança deve manter dentro do mesmo grupo. Uma forma não pode herdar de uma classe de domínio.  
  
## <a name="domain-relationships"></a>Relações de domínio  
 Elementos de modelo podem ser vinculados por relações. Links são sempre binários; vinculados exatamente dois elementos. No entanto, qualquer elemento pode ter vários links para outros objetos, e ainda pode haver mais de um vínculo entre o mesmo par de elementos.  
  
 Assim como você pode definir classes diferentes de elementos, você pode definir classes diferentes de links. A classe de um link é chamada uma *relacionamento de domínio*. Uma relação de domínio especifica quais classes de elemento suas instâncias podem se conectar. Cada extremidade de uma relação é chamada um *função*, e a relação de domínio define nomes para as duas funções, bem como para a própria relação.  
  
 Há dois tipos de relações entre domínios: inserindo relações e relações de referência. No diagrama de definição de DSL, relações de incorporação têm linhas sólidas em cada função e relações de referência tem tracejado linhas.  
  
### <a name="embedding-relationships"></a>Inserção de relações  
 Cada elemento em um modelo, exceto para sua raiz é o destino de um link de inserção. Portanto, o modelo inteiro forma uma única árvore de inserção de links. Um relacionamento de incorporação representa confinamento ou propriedade. Dois elementos que estão relacionados dessa maneira são também conhecidos como pai e filho. O filho deve ser inserido no pai.  
  
 Links de incorporação não são normalmente mostradas explicitamente como conectores em um diagrama. Em vez disso, eles geralmente são representados por confinamento. A raiz do modelo é representada pelo diagrama e elementos inseridos nele são exibidos como formas no diagrama.  
  
 No exemplo, a classe raiz música tem uma relação de incorporação MusicHasAlbums álbum, que tem um AlbumHasSongs incorporação música. Músicas são exibidas como itens em uma lista dentro de cada álbum. Música também tem um MusicHasArtists incorporada à classe artista, cujas instâncias também aparecem como formas no diagrama.  
  
 Por padrão, os elementos inseridos automaticamente são excluídos quando seus pais são excluídos.  
  
 Quando um modelo é salvo no arquivo em formato XML, os elementos inseridos são aninhados dentro de seus pais, a menos que você personalizou a serialização.  
  
> [!NOTE]
>  Incorporação não é o mesmo que herança. Filhos em um relacionamento de incorporação não herdam as propriedades do pai. Uma inserção é um tipo de link entre os elementos de modelo. Herança é uma relação entre classes e não criar links entre elementos de modelo.  
  
### <a name="embedding-rules"></a>Regras de incorporação  
 Cada elemento em um modelo de instância deve ser o destino de link de incorporação exatamente um, exceto para a raiz do modelo.  
  
 Portanto, cada classe de domínio não-abstrato, exceto a classe raiz, deve ser o destino de pelo menos um relacionamento de incorporação ou ele deve herdar de uma inserção de uma classe base. Uma classe pode ser o destino de dois ou mais objetos incorporados, mas seus elementos de modelo de instância só podem ter um pai de cada vez. A multiplicidade de destino para a origem deve ser entre 0 e 1 ou 1..1.  
  
### <a name="the-explorer-displays-the-embedding-tree"></a>O Pesquisador de objetos exibe a árvore de incorporação  
 A definição de DSL também cria um pesquisador de objetos, os usuários veem junto com seus diagramas de modelo.  
  
 ![Pesquisador de objetos gerado de DSL](../modeling/media/music_explorer.png "Music_Explorer")  
  
 O Pesquisador de objetos mostra todos os elementos no modelo, mesmo aqueles para os quais você não definiu nenhuma forma. Ele mostra os elementos e relações incorporação, mas não relações de referência.  
  
 Para ver os valores das propriedades do domínio de um elemento, o usuário seleciona um elemento, no diagrama de modelo ou no Gerenciador de modelos e abre a janela Propriedades. Ele exibe todas as propriedades de domínio, incluindo aqueles que não são exibidos no diagrama. No exemplo, cada música tem um título e um gênero, mas apenas o valor do título é mostrado no diagrama.  
  
## <a name="reference-relationships"></a>Relações de referência  
 Uma relação de referência representa qualquer tipo de relação que não está inserindo.  
  
 Relações de referência normalmente são exibidas em um diagrama que os conectores entre as formas.  
  
 Na representação XML do modelo, um link de referência entre dois elementos é representado usando *identificadores de origem.* Ou seja, identificadores são nomes que identificam exclusivamente cada elemento no modelo. O nó XML para cada elemento de modelo contém um nó que especifica o nome da relação e o moniker do outro elemento.  
  
## <a name="roles"></a>Funções  
 Cada relação de domínio tem duas funções, uma função de origem e uma função de destino.  
  
 Na figura a seguir, a linha entre o **publicador** classe de domínio e o **PublisherCatalog** relacionamento de domínio é a função de origem. A linha entre o relacionamento de domínio e o **álbum** classe de domínio é a função de destino.  
  
 ![Funções e propriedades. ] (../modeling/media/propertycode.png "PropertyCode")  
  
 Os nomes associados a uma relação são especialmente importantes quando você escreve o código do programa que atravessa o modelo. Por exemplo, quando você compila a solução DSL, a classe gerada Publisher tem uma propriedade catálogo é uma coleção de álbuns. A classe álbum tem uma propriedade do publicador é uma única instância da classe publicador.  
  
 Quando você cria uma relação em uma definição de DSL, os nomes de propriedade e relação recebem valores padrão. No entanto, você pode alterá-los.  
  
## <a name="multiplicities"></a>Multiplicidades  
 Multiplicidades especifique quantos elementos pode ter a mesma função em um relacionamento de domínio. No exemplo, os zero-para-muitos (0...\*) configuração multiplicidade de **catálogo** função especifica que qualquer instância do **publicador** classe de domínio pode ter tantos  **PublisherCatalog** relação links que você deseja atribuir a ela.  
  
 Configurar a multiplicidade de uma função digitando no diagrama ou modificando o `Multiplicity` propriedade o **propriedades** janela. A tabela a seguir descreve as configurações para essa propriedade.  
  
|Tipo de multiplicidade|Descrição|  
|-----------------------|-----------------|  
|0.. * (zero para muitos)|Cada instância da classe de domínio pode ter várias instâncias da relação ou nenhuma instância da relação.|  
|Entre 0 e 1 (zero para um)|Cada instância da classe de domínio pode ter não mais de uma instância da relação ou nenhuma instância da relação.|  
|1..1 (um)|Cada instância da classe de domínio pode ter uma instância da relação. Você não pode criar mais de uma instância do relacionamento de qualquer instância da classe de função. Se a validação é ativada, um erro de validação será exibido quando qualquer instância da classe de função não tenha nenhuma instância da relação.|  
|1.. * (um para muitos)|Cada instância da classe na função que possui essa multiplicidade pode ter várias instâncias da relação, e cada instância deve ter pelo menos uma instância da relação. Se a validação é ativada, um erro de validação será exibido quando qualquer instância da classe de função não tenha nenhuma instância da relação.|  
  
## <a name="domain-relationships-as-classes"></a>Relações de domínio como Classes  
 Um link é representado no repositório como uma instância de LinkElement, que é uma classe derivada de ModelElement. Você pode definir essas propriedades no diagrama de modelo de domínio em relações de domínio.  
  
 Você também pode fazer uma relação de origem ou destino de outras relações. No diagrama de modelo de domínio, clique com botão direito do relacionamento de domínio e, em seguida, clique em **mostram como a classe**. Será exibida uma caixa de classe adicional. Em seguida, você pode conectar relações a ela.  
  
 Você pode definir uma relação em parte pela herança, exatamente como faria com classes de domínio. Selecione a relação derivada e defina **relação de Base** na janela Propriedades.  
  
 Uma relação derivada especializada sua relação de base. Classes de domínio que ele links deve ser derivados de ou igual as classes vinculadas pela relação de base. Quando um link da relação derivada é criado em um modelo, ele é uma instância de derivada e as relações base. No código do programa, você pode navegar para a outra ponta do link usando as propriedades geradas com a base ou pela classe derivada.  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
