---
title: "Diagramas de dependência: Referência | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: "33"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: 43901987c9f6f37e7082200f675549021fb63f83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="dependency-diagrams-reference"></a>Diagramas de dependência: referência
No Visual Studio, você pode usar um *diagrama de dependência* para visualizar a arquitetura de alto nível, a lógica do seu sistema. Um diagrama de dependência organiza os artefatos físicos no seu sistema em grupos lógicos, abstract chamados *camadas*. Essas camadas descrevem as tarefas principais que executam os artefatos ou os principais componentes do seu sistema. Cada camada também pode conter camadas aninhadas que descrevem as tarefas mais detalhadas.  
  
 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Você pode especificar as dependências existentes ou pretendidas entre camadas. Essas dependências, que são representadas como setas, indicam quais camadas podem usar ou utilizam a funcionalidade representada por outras camadas. Organizando o sistema em camadas que descrevem as funções distintas de um diagrama de dependência pode ajudar a tornar mais fácil para você entender, reutilizar e manter seu código.  
  
 Use um diagrama de dependência para ajudá-lo a executar as seguintes tarefas:  
  
-   Comunicar-se a arquitetura lógica existente ou pretendida do seu sistema.  
  
-   Detecte conflitos entre seu código existente e a arquitetura pretendida.  
  
-   Visualize o impacto das alterações na arquitetura pretendida quando refatorar, atualizar ou desenvolver seu sistema.  
  
-   Reforçar a arquitetura pretendida durante o desenvolvimento e manutenção do seu código, incluindo a validação com seu check-in e operações de compilação.  
  
 Este tópico descreve os elementos que você pode usar em um diagrama de dependência. Para obter mais informações sobre como criar e desenhar diagramas de dependência, consulte [diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md). Para obter mais informações sobre os padrões de camadas, visite o [padrões e práticas de site](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-dependency-diagrams"></a>Diagramas de dependência de leitura  
 ![Elementos em diagramas de dependência](../modeling/media/uml_layerrefreading.png "UML_LayerRefReading")  
  
 A tabela a seguir descreve os elementos que você pode usar em um diagrama de dependência.  
  
|**Forma**|**Elemento**|**Descrição**|  
|---------------|-----------------|---------------------|  
|1|**Camada**|Um grupo lógico de artefatos físicos no seu sistema. Esses artefatos podem ser projetos, namespaces, classes, métodos e assim por diante.<br /><br /> Para ver os artefatos que estão vinculados a uma camada, abra o menu de atalho para a camada e escolha **Exibir Links** abrir **Explorer camada**.<br /><br /> Para obter mais informações, consulte [Explorer camada](#Explorer).<br /><br /> -   **Proibido dependências de Namespace** -Especifica que os artefatos associados a essa camada não podem depender de namespaces especificados.<br />-   **Proibido Namespaces** -Especifica que os artefatos associados a essa camada não devem pertencer aos namespaces especificados.<br />-   **Necessário Namespaces** -Especifica que os artefatos associados a essa camada devem pertencer a um dos namespaces especificados.|  
|2|**Dependência**|Indica que uma camada pode usar a funcionalidade em outra camada, mas não vice-versa.<br /><br /> -   **Direção** -Especifica a direção da dependência.|  
|3|**Dependência bidirecional**|Indica que uma camada pode usar a funcionalidade em outra camada e vice-versa.<br /><br /> -   **Direção** -Especifica a direção da dependência.|  
|4|**Comentário**|Use para adicionar anotações gerais para o diagrama ou a elementos do diagrama.|  
|5|**Link de comentário**|Use para vincular comentários a elementos do diagrama.|  
  
##  <a name="Explorer"></a>Gerenciador de camada  
 Você pode vincular cada camada para artefatos em sua solução, como projetos, classes, namespaces, arquivos de projeto e outras partes do seu software. O número em uma camada mostra o número de artefatos que estão vinculados à camada. No entanto, ao ler o número de artefatos em uma camada, lembre-se do seguinte:  
  
-   Se uma camada estiver vinculada a um artefato que contenha outros artefatos, mas não estiver vinculada diretamente a outros artefatos, o número incluirá apenas o artefato vinculado. No entanto, os outros artefatos estão incluídos para análise durante a validação da camada.  
  
     Por exemplo, se uma camada estiver vinculada a um único namespace, o número de artefatos vinculados será 1, mesmo se o namespace contiver classes. Se a camada também tiver links para cada classe no namespace, o número incluirá as classes vinculadas.  
  
-   Se uma camada contiver outras camadas vinculadas a artefatos, a camada de contêiner também estará vinculada a esses artefatos, mesmo que o número na camada de contêiner não inclua esses artefatos.  
  
 Para obter mais informações sobre a vinculação de camadas e artefatos, consulte:  
  
-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)  
  
-   [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>Para examinar os artefatos vinculados  
  
-   No diagrama de dependência, abra o menu de atalho para uma ou mais camadas e, em seguida, escolha **Exibir Links**.  
  
     **Pesquisador de objetos da camada** é aberto e mostra os artefatos que estão vinculados a camadas selecionadas. **Pesquisador de objetos da camada** tem uma coluna que mostra cada uma das propriedades dos links de artefato.  
  
    > [!NOTE]
    >  Se você não veja todas essas propriedades, expanda o **camada Explorer** janela.  
  
    |**Coluna no Gerenciador de camada**|**Descrição**|  
    |----------------------------------|---------------------|  
    |**Categorias**|O tipo de artefato, como uma classe, namespace, arquivo de origem e assim por diante|  
    |**Camada**|A camada que contém links para o artefato|  
    |**Oferece suporte à validação**|Se **True**, em seguida, o processo de validação de camada pode verificar que o projeto está de acordo com as dependências de ou para este elemento.<br /><br /> Se **False**, em seguida, o link não participar no processo de validação de camada.<br /><br /> Para obter mais informações, consulte [diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md).|  
    |**Identificador**|A referência para o artefato vinculado|  
  
## <a name="see-also"></a>Consulte também  
 [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)
