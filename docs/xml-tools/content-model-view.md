---
title: Exibição do modelo de conteúdo do Designer de Esquema XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 355fe0485327c5c92441cd54d42253d022c7bb6e
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2018
---
# <a name="content-model-view"></a>O modo do modelo de conteúdo

A exibição do modelo de conteúdo fornece uma representação gráfica de nós locais e globais de esquema e seus componentes, de incluir simples e tipos complexos, de elementos, grupos de modelo, de atributos, e de grupos de atributo. Comentários e instruções de processamento XML não podem ser exibidos no modo do modelo de conteúdo. O modo de exibição do modelo de conteúdo contém dois painéis: um **espaço de trabalho** painel que contém uma lista de nós a [espaço de designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md)e a superfície de design em que você pode ver o modelo de conteúdo do esquema nós que são selecionados no **espaço de trabalho** painel. A exibição do modelo de conteúdo também inclui a barra de ferramentas do designer de esquema XML e a barra de rastreamento.

 Na imagem a seguir, o **espaço de trabalho** painel contém seis nós de esquema. O `purchaseOrder` nó é selecionado no **espaço de trabalho** painel e é exibido na superfície de design.

 ![Exibição de Designer de modelo de conteúdo de esquema XML](../xml-tools/media/xsddesigner_contentmodelview.gif "XSDDesigner_ContentModelView")

## <a name="workspace-panel"></a>Painel de espaço de trabalho

 Depois de adicionar nós ao espaço de trabalho, a lista de nós aparecerá no **espaço de trabalho** painel de exibição do conteúdo do modelo. Quando você seleciona nós o **espaço de trabalho** do painel, eles aparecem na superfície de design de exibição do modelo de conteúdo. Para excluir nós do espaço de trabalho, use a barra de ferramentas do Designer de XSD, o **espaço de trabalho** menu de contexto do painel, ou o **excluir** chave.

 Para obter informações sobre a adição de nós, consulte a seção "Adicionando nós para o espaço de trabalho" [espaço de designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Superfície de design

 Quando um nó é selecionado no **espaço de trabalho** painel, ele é adicionado à superfície de design de exibição do modelo de conteúdo onde você pode exibir os detalhes do nó.

 O modelo de conteúdo de um nó é representado por uma árvore gráfico expansível com elementos e atributos que aparecem como nós de árvore. Por padrão, somente um nível é expandido. Outras informações, como compositores, nomes de tipo, grupos, e outros contêineres é colocada em uma barra vertical (quando expandido) ao longo de elementos e atributos que incluem. Quando você clica duas vezes em uma barra vertical, transformações horizontal e recolhe de árvore. Quando você clica duas vezes em uma barra horizontal e vertical, transformações a árvore expande. Selecionar a barra vertical seleciona todos os nós no contêiner. Expansores aparecerem à direita de um nó, se um elemento pode ser expandido ou recolhido.

 Se a superfície de design é em branco, o Editor de XML, o **XML Schema Explorer**, e a marca d'água são mostradas. O *marca d'água* é uma lista de links para todas as exibições de Designer de XSD. Se o esquema tem erros, o seguinte texto é exibido no fim da lista: “Use Lista de erros para exibir e corrigir erros no conjunto.”

## <a name="breadcrumb-bar"></a>Barra de navegação estrutural

 A barra de rastreamento na parte inferior do modo de modelo de conteúdo mostra onde o nó selecionado é localizado no conjunto de esquema.

## <a name="context-menus"></a>Menus de contexto

 Quando você clica um item na superfície de design ou **espaço de trabalho** do painel, é exibido um menu de contexto. A tabela a seguir descreve as opções que estão disponíveis para a superfície de design do modo de modelo de conteúdo.

|Opção|Descrição|
|------------|-----------------|
|**Mostrar no XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|
|**Mostrar na exibição de gráfico**|Alterna a O modo de gráfico.|
|**Gerar XML de exemplo**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|
|**Mostrar documentação**|Mostra ou de anotação/documentação de oculta conteúdo do nó.|
|**Exportar diagrama como imagem**|Salva a superfície de design para um arquivo XPS.|
|**Modo de exibição de código**|Abre o arquivo que contém o nó selecionado no editor XML. O item selecionado no **XML Schema Explorer** também é selecionado no Editor de XML.|
|**Janela Propriedades**|Abre o **propriedades** janela (se ainda não estiver aberto). Esta janela exibe informações sobre o nó.|

 A tabela a seguir descreve as opções que estão disponíveis para o **espaço de trabalho** painel.

|Opção|Descrição|
|------------|-----------------|
|**Mostrar no XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|
|**Mostrar na exibição de gráfico**|Alterna para representar graficamente a exibição.|
|**Limpar o espaço de trabalho**|Limpa o espaço de trabalho e a superfície de design.|
|**Remover do espaço de trabalho**|Removes selecionou nós de espaço de trabalho e da superfície de design.|
|**Remova todos, exceto a seleção do espaço de trabalho**|Remove os nós que não são selecionados de espaço de trabalho e da superfície de design.|
|**Gerar XML de exemplo**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|
|**Selecionar tudo**|Seleciona todos os nós a **espaço de trabalho** painel.|
|**Modo de exibição de código**|Abre o arquivo que contém o nó selecionado no editor XML. O item selecionado no **XML Schema Explorer** também é selecionado no Editor de XML.|
|**Janela Propriedades**|Abre o **propriedades** janela (se ainda não estiver aberto). Esta janela exibe informações sobre o nó.|

## <a name="properties-window"></a>Janela de Propriedades

 Use o menu de contexto para abrir inicialmente o **propriedades** janela. Por padrão, o **propriedades** janela aparece no canto inferior direito do Visual Studio. Quando você clica em um nó que é renderizado no modo de exibição de modelo de conteúdo, as propriedades de nó são exibidas no **propriedades** janela.

## <a name="xsd-designer-toolbar"></a>Barra de ferramentas designer de XSD

 Os seguintes botões da barra de ferramentas do designer XSD são ativados quando a exibição do modelo de conteúdo está ativo.

 ![Ferramentas de Designer de esquema XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")

|Opção|Descrição|
|------------|-----------------|
|**Mostrar o modo de início**|Alterna para o [Iniciar modo de exibição](../xml-tools/start-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl**+**1**.|
|**Mostrar exibição do modelo de conteúdo**|Alterna para o [exibição do modelo de conteúdo](../xml-tools/content-model-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl**+**2**.|
|**Mostrar exibição do gráfico**|Alterna para o [Graph exibição](../xml-tools/graph-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl**+**3**.|
|**Limpar o espaço de trabalho**|Limpa o espaço de trabalho e a superfície de design.|
|**Remover do espaço de trabalho**|Removes selecionou nós de espaço de trabalho e da superfície de design.|
|**Remova todos, exceto a seleção do espaço de trabalho**|Remove os nós que não são selecionados de espaço de trabalho e da superfície de design.|
|**Mostrar documentação**|Mostra ou de anotação/documentação de oculta conteúdo do nó.|

## <a name="panscroll"></a>Bandeja/rolagem

 Você pode deslocar a superfície de design usando as barras de rolagem ou mantendo a **Ctrl** pressionada enquanto você clique e arraste o mouse. Quando você panorâmica usando clicar e arrastar a superfície de design, o cursor muda para quatro transversais setas apontando em quatro direções.

## <a name="undoredo"></a>Desfazer/refazer

 Desfazer/refaz o recurso é habilitado no modo de modelo de conteúdo para as seguintes ações:

-   Adicionando um único nó arrastando e soltando-se.

-   Adicionando mais nós da janela de resultados de pesquisa no esquema Explorer.

-   Adicionando a exibição de nós do início.

-   Excluindo única ou mais nós.

## <a name="zoom"></a>Aplicar Zoom

 Zoom está disponível no canto inferior direito da exibição do conteúdo do modelo.

 O zoom pode ser controlado das seguintes maneiras:

-   Mantendo o **Ctrl** chave e girando o mouse wheel quando o mouse passa sobre a superfície de exibição do modelo de conteúdo.

-   Usando o controle deslizante. O controle deslizante mostra o nível atual de zoom.

O controle deslizante de Zoom é opaco ao selecioná-lo, passe o mouse sobre ele ou usar **Ctrl** com a roda do mouse para ampliar; todas as outras vezes, isso é transparente.

## <a name="xml-editor-integration"></a>Integração do editor de XML

 Você pode alternar entre o **XSD Designer** e o Editor de XML usando o menu de contexto.

 Se você fizer alterações no esquema definido no Editor de XML, as alterações serão sincronizadas no modo de exibição de modelo de conteúdo. Para obter mais informações, consulte [integração com o editor de XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Consulte também

- [O espaço de trabalho do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md)