---
title: Visualizar código
ms.date: 11/04/2016
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c1061d7369bbd73232ceb15dd71db203ee392da
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="visualize-code"></a>Visualizar código
Você pode usar a visualização e modelagem de ferramentas no Visual Studio para ajudá-lo a entender o código existente e descrever seu aplicativo. Isso lhe permite visualmente saber como as alterações podem afetar o código e ajudam a que avaliar o trabalho e os riscos que resultam dessas alterações. Por exemplo:

-   Para entender as relações em seu código, mapeie essas relações visualmente.

-   Para descrever a arquitetura do sistema e manter o código consistente com seu design, criar diagramas de dependência e validar o código em relação a esses diagramas.

-   Para descrever estruturas de classe, crie diagramas de classe.

 Essas ferramentas também ajudam você a se comunicar mais facilmente com as pessoas envolvidas com o seu projeto.

 Para ver quais versões do Visual Studio oferecem suporte a cada recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

|||
|-|-|
|**Compreenda o código e suas relações:**<br /><br /> Mapear relações entre partes específicas de código.<br /><br /> Consulte uma visão geral das relações em seu código para toda a solução.<br /><br /> **Observação**: nesta versão do Visual Studio, o termo *mapa de códigos* é usado no lugar de *gráfico de dependência*.|-   [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Encontrar possíveis problemas usando analisadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Mapear métodos na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Compreenda as estruturas de classe:**<br /><br /> Visualize a estrutura de classes em um projeto Criando diagramas de classe do código.|[Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Descrever o design de alto nível do sistema e validar o código em relação a esse design:**<br /><br /> Descreva o design de alto nível do sistema e suas dependências pretendidas Criando diagramas de dependência. Valide o código em relação a esse design e verifique se as dependências no código permanecem consistentes com o design.|-   [Criar diagramas de dependência do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar o código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoria**|**Links**|
|------------------|---------------|
|**Fóruns**|-   [Visualização do Visual Studio e ferramentas de modelagem](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visualização do Visual Studio e modelagem SDK (ferramentas DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogs**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**Diários e artigos técnicos**|[Fórum do MSDN arquitetura](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Consulte também

- [Cenário: alterar o design usando visualização e modelagem](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Análise e modelagem de arquitetura](../modeling/analyze-and-model-your-architecture.md)
- [Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)
- [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
