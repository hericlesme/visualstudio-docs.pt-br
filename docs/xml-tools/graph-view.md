---
title: Exibição do gráfico do Designer de Esquema XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a6ad12c823d0a29bb2d4211f03010e484e79257
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751696"
---
# <a name="graph-view"></a>Exibição de gráfico

A exibição do gráfico fornece uma representação gráfica de nós globais do esquema e relações entre os nós. Observe que a exibição do gráfico não permite que você alterar o layout do esquema definido na superfície de design. A exibição do gráfico também inclui a barra de ferramentas do designer de esquema XML e a barra de rastreamento.

 A imagem a seguir mostra a visualização de gráfico com seis nós globais na superfície de design.

 ![Exibição do gráfico do Designer de Esquema XML](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Superfície de design

 A superfície de design do modo de exibição de gráfico exibe o conteúdo do [espaço de designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md). Se o espaço de trabalho contém quaisquer nós globais do conjunto de esquema, os nós são mostrados na superfície de design do modo de gráfico e as setas são desenhadas entre os nós que possuem relações.

 Clique duas vezes em um nó no modo de gráfico trará anterior o editor XML.

 Para excluir nós selecionados do espaço de trabalho, use a barra de ferramentas do Designer de XSD ou o **excluir** chave.

 Se a superfície de design é em branco, o Editor de XML, o **XML Schema Explorer**, e a marca d'água são mostradas. O *marca d'água* é uma lista de links para todas as exibições de Designer de XSD.

 ![Designer XSD; Exibição do gráfico](../xml-tools/media/xsdgraphviewwatermark.gif)

 Se o esquema tem erros, o seguinte texto é exibido no fim da lista: “Use Lista de erros para exibir e corrigir erros no conjunto.”

## <a name="breadcrumb-bar"></a>Barra de navegação estrutural

 A barra de rastreamento na parte inferior do modo de figura a seguir mostra onde o nó selecionado é localizado no conjunto de esquema. Se vários itens são selecionados, a barra de rastreamento será em branco.

## <a name="context-menu"></a>Menu de contexto

 A tabela a seguir descreve as opções que estão disponíveis para todos os nós na superfície de design do modo de gráfico.

|Opção|Descrição|
|------------|-----------------|
|**Mostrar no XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|
|**Mostrar na exibição de gráfico**|Alterna para o modo de exibição gráfico (desativada).|
|**Gerar XML de exemplo**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|
|**Limpar o espaço de trabalho**|Limpa o espaço de trabalho e a superfície de design.|
|**Remover do espaço de trabalho**|Removes selecionou nós de espaço de trabalho e da superfície de design.|
|**Remova todos, exceto a seleção do espaço de trabalho**|Remove os nós que não são selecionados de espaço de trabalho e da superfície de design.|
|**Exportar diagrama como imagem**|Salva a superfície de design para um arquivo XPS.|
|**Selecionar tudo**|Selecionar todos os nós na superfície de design.|
|**Modo de exibição de código**|Abre o arquivo que contém o nó selecionado no editor XML. O item selecionado no **XML Schema Explorer** também é selecionado no Editor de XML.|
|**Janela Propriedades**|Abre o **propriedades** janela (se ainda não estiver aberto). Esta janela exibe informações sobre o nó.|

 Além das opções comuns descritas anterior, o menu de contexto para elementos globais também tem as seguintes opções:

|Opção|Descrição|
|------------|-----------------|
|**Adicionar definição de tipo**|Adiciona o tipo base no diagrama.|
|**Adicione todas as referências**|Adiciona todos os nós que se referem ao elemento e desenha setas para indicar relações entre eles.|
|**Adicionar membros do grupo de substituição**|Adiciona todos os membros do grupo de substituição. Essa opção aparece na exibição se o elemento é o início ou membro de um grupo de substituição.|
|**Gerar XML de exemplo**|Gerencia um arquivo XML de exemplo para o elemento global.|

 Além das opções comuns descritas anterior, o menu de contexto para tipos complexos simples e globais globais também tem as seguintes opções:

|Opção|Descrição|
|------------|-----------------|
|**Adicionar tipo de Base**|Se o tipo selecionado é derivado de um tipo global, adiciona o tipo base do tipo selecionado.|
|**Adicione todas as referências**|Adiciona todas as referências de tipo selecionado. Isso inclui os elementos e atributos do tipo selecionado, e tipos derivados do tipo selecionado.|
|**Adicionar todos os tipos derivados**|Adiciona todos os tipos que direta e indiretamente são derivados do tipo selecionado.|
|**Adicionar todos os ancestrais**|Adiciona todos os tipos de base pai ().|

 Além das opções comuns descritas anterior, o menu de contexto para grupos globais e grupos de atributo também tem as seguintes opções:

|Opção|Descrição|
|------------|-----------------|
|**Adicione todas as referências**|Adiciona todos os nós que se referem ao grupo e desenha setas para indicar relações entre eles.|
|**Adicionar todos os membros**|Adiciona todos os membros do grupo e desenha setas para indicar relações entre eles.|

 No addtion em padrões comuns descritas anterior, o menu de contexto para atributos globais também tem as seguintes opções:

|Opção|Descrição|
|------------|-----------------|
|**Adicione todas as referências**|Adiciona todos os nós que se referem ao grupo e desenha setas para indicar relações entre eles.|

## <a name="properties-window"></a>Janela de Propriedades

 Use o menu de contexto para abrir inicialmente o **propriedades** janela. Por padrão, o **propriedades** janela aparece no canto inferior direito do Visual Studio. Quando você clica em um nó que é renderizado no modo de exibição de modelo de conteúdo, as propriedades de nó serão exibidas no **propriedades** janela.

## <a name="xsd-toolbar"></a>Barra de ferramentas XSD

 Os seguintes botões da barra de ferramentas XSD são ativados quando a exibição do gráfico está ativo.

 ![Barra de ferramentas do Designer de Esquema XML](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Opção|Descrição|
|------------|-----------------|
|**Mostrar o modo de início**|Alterna para o [Iniciar modo de exibição](../xml-tools/start-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl**+**1**.|
|**Mostrar exibição do modelo de conteúdo**|Alterna para o [exibição do modelo de conteúdo](../xml-tools/content-model-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl**+**2**.|
|**Mostrar exibição do gráfico**|Alterna para o [Graph exibição](../xml-tools/graph-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl**+**3**.|
|**Limpar o espaço de trabalho**|Limpa o espaço de trabalho e a superfície de design.|
|**Remover do espaço de trabalho**|Removes selecionou nós de espaço de trabalho e da superfície de design.|
|**Remova todos, exceto a seleção do espaço de trabalho**|Remove os nós que não são selecionados de espaço de trabalho e da superfície de design. Essa opção é ativada no modo do modelo de conteúdo e no modo de gráfico.|
|**Esquerda para a direita**|Altera o layout no modo de gráfico a uma representação hierárquica esquerda para a direita de nós. Essa opção pode ser acessada usando o atalho de teclado: **Alt**+**seta para a direita**.|
|**Direita para a esquerda**|Altera o layout no modo de gráfico a uma representação hierárquica da direita para a esquerda de nós. Essa opção pode ser acessada usando o atalho de teclado: **Alt**+**seta para a esquerda**.|
|**Cima para baixo**|Altera o layout no modo de gráfico a uma representação hierárquica de cima para baixo de nós. Essa opção pode ser acessada usando o atalho de teclado: **Alt**+**a seta para baixo**.|
|**Baixo para cima**|Altera o layout no modo de gráfico a uma representação hierárquica de parte inferior-à- parte superior dos nós. Essa opção pode ser acessada usando o atalho de teclado: **Alt**+**a seta para cima**.|

## <a name="panscroll"></a>Bandeja/rolagem

 Você pode deslocar a superfície de design usando as barras de rolagem ou mantendo a **Ctrl** pressionada enquanto você clique e arraste o mouse. Quando você filtra a superfície de design usando o clique e o arrastar, o cursor será alterado a quatro setas cruzadas apontando em quatro direções.

## <a name="undoredo"></a>Desfazer/refazer

 Desfazer/refaz o recurso é habilitado no modo de gráfico para as seguintes ações:

-   Adicionando um único nó arrastando e soltando-se.

-   Adicionando mais nós da janela de resultados de pesquisa no esquema Explorer ou em consultas de exibição de Início.

-   Excluindo única ou mais nós.

## <a name="zoom"></a>Aplicar Zoom

 O zoom está disponível no canto inferior direito do modo de gráfico.

 O zoom pode ser controlado das seguintes maneiras:

-   Mantendo o **Ctrl** chave e girando o mouse wheel quando o mouse passa sobre a superfície de exibição do gráfico.

-   Usando o controle deslizante. O controle deslizante mostra o nível atual de zoom.

O controle deslizante de Zoom é opaco ao selecioná-lo, passe o mouse sobre ele ou usar **Ctrl** com a roda do mouse para ampliar; todas as outras vezes, isso é transparente.

## <a name="xml-editor-integration"></a>Integração do editor de XML

 Você pode alternar para frente e para trás entre o modo de gráfico e o editor XML clicando em um nó e usando o menu de contexto de código de exibição.

 Se você alterar o esquema definido no editor XML, as alterações serão sincronizadas no modo de gráfico. Para obter mais informações, consulte [integração com o editor de XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Consulte também

- [Superfície de design](../xml-tools/xml-schema-designer-workspace.md)