---
title: Novidades no design no Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c25d89ae3ab3d25e415b4407a46fc903b1c05266
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="whats-new-for-design-in-visual-studio"></a>Novidades no design no Visual Studio

## <a name="live-dependency-validation"></a>Validação de dependência dinâmica

Remoção de dependências indesejadas é uma parte importante de gerenciar seu débito técnico. Validação dinâmica de dependências é agora incluído, fornecendo informações precisas sobre problemas e totalmente usam os novos recursos na lista de erros e o editor.

![Validação de dependência dinâmica em ação](media/dep-validation-whatsnew-01.png)

A experiência de criação foi alterada para fazer a validação de dependência mais detectáveis e mais acessível, alterando a terminologia de "Diagrama de camada" para "Diagrama de dependência".

O **arquitetura** menu agora contém um comando para criar um diagrama de dependência:

![Item de dependência dinâmica no menu de arquitetura](media/dep-validation-whatsnew-02.png)

... e os nomes de propriedade de uma camada em um diagrama de dependência e suas descrições, foram alterados para torná-los mais significativos:

![Nomes de propriedade de dependência dinâmica atualizado](media/dep-validation-whatsnew-03.png)

Agora você ver o impacto das alterações imediatamente nos resultados da análise de código atual na solução de cada vez que você salvar o diagrama. Você não precisa aguardar a conclusão do comando "Validar dependências" mais.

Para obter mais detalhes, consulte [esta postagem de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Designers UML foram removidos

Os designers UML foram removidos dessa versão do Visual Studio Enterprise.

* Diagramas UML agora são apresentados como arquivos XML
* O Gerenciador de modelos UML não existe mais
* As referências não são mais usadas para validação de dependência de projeto de modelagem
* O nó "Camada referências" no Gerenciador de soluções não é mais exibido
* A ação de compilação "Validação" em um diagrama de dependência (camada) não é mais usada - a tarefa de compilação foi removida
* A estrutura do projeto é mantida para ciclo entre versões
* Você ainda pode abrir, criar, editar e salvar um diagrama de dependência (camada) como XML
* Itens de trabalho do TFS vinculados a um diagrama de dependência (camada) não estão acessíveis na superfície de design
* Não há suporte para a vinculação de voltar de DSL ou uma camada
* Não há suporte para extensibilidade UML no SDK de modelagem

No entanto, há suporte para visualizar a arquitetura do código do C++ e .NET disponível por meio de [mapas de código](map-dependencies-across-your-solutions.md)e os aperfeiçoamentos significativos para validação de dependência descrito acima.

Se você for um usuário significativo dos designers UML, você pode continuar a usar o Visual Studio 2015 ou versões anteriores ao decidir sobre uma ferramenta alternativa para suas necessidades UML.

Para obter mais detalhes, consulte [esta postagem de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-version-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Suporte de versão para a arquitetura e ferramentas de modelagem

Visual Studio 2015 está disponível em várias versões. Nem todos eles oferecem suporte para a arquitetura e ferramentas de modelagem. A tabela a seguir mostra a disponibilidade de cada ferramenta.

|**Recurso**|**Enterprise**|**Professional**|**Comunidade**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapas de código**|Sim|Só oferece suporte à leitura de mapas de código, filtragem código mapas, adicionar novos nós genéricos e criar um novo gráfico direcionado de uma seleção.|-|-|
|**Diagramas de dependência**|Sim|Dá suporte apenas à leitura de diagramas de dependência.|Dá suporte apenas à leitura de diagramas de dependência.|-|
|**Direcionado gráficos** (diagramas DGML)|Sim|Sim|Sim|-|
|**Clone de código**|Sim|-|-|-|