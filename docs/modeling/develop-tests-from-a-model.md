---
title: Desenvolver testes de um modelo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tests and requirements
ms.assetid: 40f87192-ba85-4552-8804-314a678261ae
caps.latest.revision: "20"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: ea0753130b6fa1da60cf83cf15c0ee5c7f4010c2
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2017
---
# <a name="develop-tests-from-a-model"></a>Desenvolver testes por meio de um modelo
Você pode usar requisitos e modelos de arquitetura para ajudá-lo a organizar os testes do seu sistema e seus componentes. Essa prática ajuda a garantir que você teste os requisitos que são importantes para os usuários e outros participantes e ajuda a atualizar os testes rapidamente quando alterarem os requisitos. Se você usar [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], você também poderá manter os links entre os modelos e os testes.  
  
 Para ver quais versões do Visual Studio oferecem suporte a esses recursos, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="system-and-subsystem-testing"></a>Sistema e o subsistema de teste  
 *Sistema de teste,* também conhecido como *testes de aceitação*, significa que se estão sendo atendidas necessidades dos usuários de teste. Esses testes preocupadas com o comportamento visível externamente do sistema em vez do design interno.  
  
 Testes de sistema são muito úteis quando estender ou recriar um sistema. Eles ajudam a evitar a introdução de erros quando você alterar o código.  
  
 Quando você planejar qualquer alteração ou a extensão de um sistema, é útil começar com um conjunto de testes de sistema que são executados em um sistema existente. Em seguida, você pode estender ou ajustar os testes para testar os novos requisitos, faça as alterações no código e execute novamente o conjunto completo de testes.  
  
 Quando você desenvolve um novo sistema, você pode começar a criar testes desde o início de desenvolvimento. Definindo testes antes de desenvolver cada recurso, você pode capturar as discussões de requisitos de uma maneira muito específica.  
  
 Subsistema de teste, os mesmos princípios se aplica aos principais componentes de um sistema. Cada componente é testado separadamente de outros componentes. Subsistema de testes se concentram no comportamento visível em interfaces de usuário ou a API do componente.  
  
## <a name="deriving-system-tests-from-a-requirements-model"></a>Derivando de testes de sistema de um modelo de requisitos  
 Você pode criar e manter uma relação entre testes de sistema e um modelo de requisitos. Para estabelecer essa relação, você pode escrever testes que correspondem para os principais elementos do modelo de requisitos. O Visual Studio ajuda a manter a relação, permitindo que você crie links entre os testes e partes do modelo. Para obter mais informações sobre modelos de requisitos, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).  
  
### <a name="write-tests-for-each-use-case"></a>Escrever testes para cada caso de uso  
 Se você usar [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], você pode criar um grupo de testes para cada caso de uso que você definiu no seu modelo de requisitos. Por exemplo, se você tiver um caso de uso ordem uma refeição, que inclui criar pedido e Adicionar Item à ordem, você pode criar testes para ambos os geral e mais detalhada desses casos de uso. 
  
 Essas diretrizes podem ser úteis:  
  
-   Cada caso de uso deve ter vários testes, para caminhos principais e resultados excepcionais.  
  
-   Quando você descreve um caso de uso no modelo de requisitos, é mais importante definir seu pós-condição, ou seja, a meta é obtida de para descrevem detalhadamente os procedimentos o usuário deve seguir para atingir a meta. Por exemplo, pode ser pós-condição da ordem uma refeição um restaurante está preparando uma refeição para um cliente e que o cliente paga. A pós-condição é o critério devem verificar seus testes.  
  
-   Base testes separados nas cláusulas separadas da pós-condição. Por exemplo, crie testes separados para notificar o restaurante da ordem e para fazer o pagamento do cliente. Essa separação tem estas vantagens:  
  
    -   Alterações em diferentes aspectos dos requisitos ocorrem com frequência independentemente. Separando os testes em diferentes aspectos dessa maneira, você tornar mais fácil atualizar os testes quando as necessidades mudarem.  
  
    -   Se o plano de desenvolvimento implementa um aspecto do caso de uso antes de outro, você pode habilitar os testes separadamente à medida que avança de desenvolvimento.  
  
-   Quando você cria os testes, separe a escolha dos dados de teste do código ou script que determina se o pós-condição foi atingida. Por exemplo, um teste de uma função aritmética simple pode ser: 4 de entrada; Verifique se a saída é 2. Em vez disso, crie o script como: escolha uma entrada; Multiplique o resultado por si só e verifique se o resultado é a entrada original. Esse estilo permite variar as entradas de teste sem alterar o corpo principal do teste.  
  
#### <a name="linking-tests-to-use-cases"></a>Testes de vinculação para casos de uso  
 Se você estiver usando [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] para criar e executar os testes, você pode organizar seus testes no requisito, caso de uso ou itens de trabalho de história de usuário. Você pode vincular esses itens para casos de uso em seu modelo de trabalho. Isso permite que você rapidamente alterações de requisitos de rastreamento para os testes e ajuda a acompanhar o progresso de cada caso de uso.  
  
###### <a name="to-link-tests-to-a-use-case"></a>Para vincular os testes a um caso de uso  
  
1.  Em [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], criar um requisito e um conjunto de testes de base nele.
  
     O requisito de que você cria é um item de trabalho em [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Ele pode ser um item de trabalho história de usuário, requisito ou caso de uso, dependendo do modelo de processo que usa o seu projeto [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Para obter mais informações, consulte [acompanhar o trabalho usando o Visual Studio Team Services ou o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Vincule o item de trabalho de requisito para um ou mais casos de uso em seu modelo.  
  
     Em um diagrama de caso de uso, clique em um caso de uso e, em seguida, clique em **Link para o Item de trabalho**. 
  
3.  Adicione para o conjunto de testes, casos de teste que verifique se os casos de uso.  
  
 Geralmente, cada item de trabalho de requisito ou história de usuário será vinculado a vários casos de uso em seu modelo, e cada caso de uso será vinculado a vários requisitos ou histórias de usuários. Isso ocorre porque cada história de usuário ou requisito abrange um conjunto de tarefas que desenvolver vários casos de uso. Por exemplo, em uma iteração anterior do projeto, você pode desenvolver a história de usuário básico no qual um cliente pode escolher itens de um catálogo e entregues. Em uma iteração mais recente, o texto pode ser que o usuário paga quando concluir a ordem e o fornecedor recebe o dinheiro depois que ele envia as mercadorias.  Cada história adiciona uma cláusula para pós-condição do caso de uso de produtos de ordem.  
  
 Você pode criar links separados de requisitos para cláusulas da pós-condição escrevendo as cláusulas em comentários separados no diagrama de caso de uso. Você pode vincular cada comentário a um item de trabalho de requisito e vincular o comentário para o caso de uso no diagrama.  
  
### <a name="base-tests-on-the-requirements-types"></a>Testes de base nos tipos de requisitos  
 Os tipos, que é, as classes, interfaces e enumerações de um modelo de requisitos descrevem os conceitos e as relações em termos de como os usuários pensam e se comunicar sobre seus negócios. Ele exclui tipos preocupados apenas com o design interno do sistema.  
  
 Os testes em termos desses tipos de requisitos de design. Essa prática ajuda a garantir que, quando as alterações nos requisitos são discutidas, é fácil relacionar as alterações para as alterações necessárias nos testes. Ele possibilita a discutir os testes e seus resultados pretendidos diretamente com os usuários finais e outros participantes. Isso significa que os usuários precisam podem ser mantidos fora do processo de desenvolvimento e evita o design acidental dos testes em torno de possíveis falhas no design.  
  
 Para testes manuais, essa prática envolve cumprir o vocabulário do modelo requisitos nos scripts de teste. Para testes automatizados, essa prática envolve usando os diagramas de classe requisitos como base para o código de teste e criar acessador e updater funções para vincular o modelo de requisito para o código.  
  
 Por exemplo, requisitos de um modelo pode incluir tipos de Menu, Item de Menu, ordem e associações entre elas. Este modelo representa as informações que são armazenadas e tratadas pela refeição sistema de pedidos, mas não representam as complexidades de sua implementação. No sistema de trabalho, pode haver vários realizações diferentes de cada tipo, em bancos de dados, nas interfaces do usuário e nas APIs. Em um sistema distribuído, pode haver diversas variantes de cada instância sejam armazenados em diferentes partes do sistema ao mesmo tempo.  
  
 Para testar um caso de uso, como adicionar Item à ordem, um método de teste pode incluir código semelhante a este:  
  
```  
Order order = ... ; // set up an order  
// Store prior state:  
int countBefore = order.MenuItems.Count;   
// Perform use case:  
MenuItem chosenItem = ...; // choose an item  
AddItemToOrder (chosenItem, order);   
// Verify part of postcondition:  
int countAfter = order.MenuItems.Count;  
Assert (countAfter == countBefore = 1);   
```  
  
 Observe que esse método de teste usa as classes de modelo de requisitos. Associações e os atributos são obtidos como propriedades do .NET.  
  
 Para executar esse trabalho, as propriedades das classes devem ser definidas como somente leitura de funções ou acessadores, que acessa o sistema para recuperar informações sobre seu estado atual. Métodos simulam casos de uso, como AddItemToOrder devem direcionar o sistema por meio de sua API ou uma camada sob sua interface do usuário. Os construtores de objetos de teste como ordem e MenuItem também devem direcionar o sistema para criar itens correspondentes no sistema.  
  
 Muitos dos acessadores e atualizadores já estará disponíveis por meio da API normal do aplicativo. Mas algumas funções adicionais podem ser gravados para permitir que os testes. Esses atualizadores e os acessadores adicionais também são conhecidas como 'teste instrumentação'. Porque eles dependem do design interno do sistema, é responsabilidade de desenvolvedores do sistema para fornecê-los, enquanto os testadores escrevem o código dos testes em termos de modelo de requisitos.  
  
 Quando você escrever testes automatizados, você pode usar testes genéricos para encapsular os acessadores e atualizadores.
  
### <a name="tests-for-business-rules"></a>Testes para regras de negócios  
 Alguns requisitos não estão diretamente relacionados a qualquer um caso de uso. Por exemplo, o negócio DinnerNow permite que os clientes de muitos Menus, mas requer que cada ordem, todos os itens devem ser de um único Menu escolhido. Essa regra de negócio pode ser expresso como uma constante sobre as associações entre os pedidos, Menus e itens no modelo de classe de requisitos.  
  
 Uma regra invariável desse tipo controla não apenas a todos os casos de uso são definidos no momento, mas também quaisquer outros casos de uso que serão definidos posteriormente. Portanto, é útil para gravá-lo separadamente de um caso de uso e testá-lo separadamente dos casos de uso.  
  
## <a name="deriving-subsystem-tests-from-models"></a>Derivando de testes do subsistema de modelos  
 No design de alto nível de um sistema grande, você pode identificar componentes ou subsistemas. Eles representam partes que podem ser criados separadamente, estão localizados em diferentes computadores ou são módulos reutilizáveis que podem ser recombined de várias maneiras. 
  
 Você pode aplicar a cada componente principal os mesmos princípios que você usa em todo o sistema. Em um projeto grande, cada componente pode ter seu próprio modelo de requisitos. Em projetos menores, um modelo de arquitetura ou design de alto nível pode ser criado para mostrar os principais componentes e suas interações. Para obter mais informações, consulte [modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md).  
  
 Em ambos os casos, você pode estabelecer uma relação entre os elementos de modelo e os testes de subsistema da mesma maneira como você faria entre o modelo de requisitos e os testes de sistema.  
  
### <a name="isolate-components-with-provided-and-required-interfaces"></a>Isolar componentes com as Interfaces necessárias e fornecidos  
 É útil para identificar todas as dependências que tem um componente em outras partes do seu sistema ou serviços externos e para representar esses como Interfaces necessárias. Este exercício geralmente leva a alguns reestruturação que deixa o componente facilmente separáveis e muito mais separado do restante do seu design.  
  
 Uma vantagem dessa desassociação é que o componente pode ser executado para teste, substituindo por objetos fictícios os serviços que normalmente usa. Esses são os componentes que são configurados para fins de teste. Um componente fictício fornece a interface que requer que seu componente, respondendo a consultas com dados simulados. Os componentes de simulações fazem parte de um conjunto de teste completo que você pode se conectar a todas as interfaces do componente.  
  
 Um benefício de teste de simulação é que você pode desenvolver seu componente enquanto os outros componentes cujos usará os serviços ainda estão em desenvolvimento.  
  
## <a name="maintain-the-relationships-between-tests-and-model"></a>Manter as relações entre testes e modelo  
 Em um projeto típico que executa uma iteração de tempos em tempos, uma análise dos requisitos é mantida próximo ao início de cada iteração. Reunião aborda os recursos que devem ser entregues na próxima iteração. Um modelo de requisitos pode ser usado para ajudar a discutir os conceitos, cenários e sequências de ações que serão desenvolvidas. Os stakeholders business definir prioridades, os desenvolvedores fazem estimativas e os testadores garantir que o comportamento esperado de cada recurso é capturado corretamente.  
  
 Escrevendo testes é a maneira mais eficiente para definir um requisito, e também é uma maneira eficiente de garantir que uma pessoa tenha uma compreensão clara de que é necessário. No entanto, enquanto os testes de gravação levar muito tempo para fazer durante um workshop de especificação, criação de modelos pode ser feito muito mais rapidamente.  
  
 Do ponto de vista teste, um modelo de requisitos pode ser visto como uma abreviação para os testes. Portanto, é importante manter a relação entre testes e o modelo em todo o projeto.  
  
##  <a name="Attaching"></a>Anexando casos de teste para elementos do modelo  
 Se seu projeto usa [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], você pode vincular os testes para os elementos em seu modelo. Isso permite que você localize rapidamente os testes afetados por alterações nos requisitos e ajuda a acompanhar a extensão à qual um requisito foi percebido.  
  
 Você pode vincular os testes para todos os tipos de elemento. Estes são alguns exemplos:  
  
-   Vincule um caso de uso para os testes que exercício-lo.  
  
-   Gravar as cláusulas de pós-condição casos de uso ou meta, para comentários que estão vinculados ao caso de uso, e, em seguida, vincule testes a todos os comentários.  
  
-   Escrever regras invariáveis em comentários em diagramas de classe ou diagramas de atividade e vinculá-los para testes.  
  
-   Testes de link para um diagrama de atividade ou atividades individuais.  
  
-   Vincule a um conjunto de testes para o componente ou o subsistema que ele testa.  
  
#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Para vincular os testes a um elemento de modelo ou a relação  
  
1.  Em [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], criar um requisito e um conjunto de testes de base nele. 
  
     O requisito de que você cria é um item de trabalho em [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Ele pode ser um item de trabalho história de usuário, requisito ou caso de uso, dependendo do modelo de processo que usa o seu projeto [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Para obter mais informações, consulte [acompanhar o trabalho usando o Visual Studio Team Services ou o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Vincule o item de trabalho de requisito para um ou mais elementos em seu modelo.  
  
     Em um diagrama de modelagem, clique em um elemento, comentário ou relação e, em seguida, clique em **Link para o Item de trabalho**.
  
3.  Adicione para o conjunto de testes, casos de teste que verifique se o requisito expressado no elemento do modelo.  
  
## <a name="see-also"></a>Consulte também  
 [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)   
 [Requisitos do modelo de usuário](../modeling/model-user-requirements.md)   
 [Modelo de arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)   
 [Análise e modelagem de arquitetura](../modeling/analyze-and-model-your-architecture.md)
