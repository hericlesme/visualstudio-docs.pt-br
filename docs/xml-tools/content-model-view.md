---
title: "Exibição do modelo de conteúdo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 582082504b713988039af609d59150715f75ecfe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="content-model-view"></a>O modo do modelo de conteúdo
A exibição do modelo de conteúdo fornece uma representação gráfica de nós locais e globais de esquema e seus componentes, de incluir simples e tipos complexos, de elementos, grupos de modelo, de atributos, e de grupos de atributo. Comentários e instruções de processamento XML não podem ser exibidos no modo do modelo de conteúdo. O modo de exibição do modelo de conteúdo contém dois painéis: um **espaço de trabalho** painel que contém uma lista de nós a [espaço de trabalho de Designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md)e a superfície de design em que você pode ver o modelo de conteúdo do esquema nós que são selecionados no **espaço de trabalho** painel. A exibição do modelo de conteúdo também inclui a barra de ferramentas do designer de esquema XML e a barra de rastreamento.  
  
 Na figura a seguir, o painel de espaço de trabalho contém seis nós de esquema. O nó de `purchaseOrder` é selecionado no painel de Workpace e exibido na superfície de design.  
  
 ![Exibição de Designer de modelo de conteúdo de esquema XML](../xml-tools/media/xsddesigner_contentmodelview.gif "XSDDesigner_ContentModelView")  
  
## <a name="workspace-panel"></a>Painel de espaço de trabalho  
 Depois de adicionar nós ao espaço de trabalho, a lista de nós aparecerá no **espaço de trabalho** painel de exibição do conteúdo do modelo. Quando você seleciona nós o **espaço de trabalho** do painel, eles aparecem na superfície de design de exibição do modelo de conteúdo. Para excluir nós do workpsace, use a barra de ferramentas do Designer de XSD, o **espaço de trabalho** menu de contexto do painel, ou a tecla DELETE.  
  
 Para obter informações sobre a adição de nós, consulte a seção "Adicionando nós para o espaço de trabalho" [espaço de trabalho de Designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md).  
  
## <a name="design-surface"></a>A superfície de design  
 Quando um nó é selecionado no painel de espaço de trabalho, ele é adicionado para a superfície de design do modo de modelo de conteúdo onde você pode exibir os detalhes do nó.  
  
 O modelo de conteúdo de um nó é representado por uma árvore gráfico expansível com elementos e atributos que aparecem como nós de árvore. Por padrão, somente um nível é expandido. Outras informações, como compositores, nomes de tipo, grupos, e outros contêineres é colocada em uma barra vertical (quando expandido) ao longo de elementos e atributos que incluem. Quando você clica duas vezes em uma barra vertical, transformações horizontal e recolhe de árvore. Quando você clica duas vezes em uma barra horizontal e vertical, transformações a árvore expande. Selecione a barra vertical selecionar todos os nós do contêiner. Os expansores aparecerão no direito de um nó se um elemento pode ser expandido ou recolhido.  
  
 Se a superfície de design está em branco, o editor XML, XML Schema Explorer, e a marca de agua são mostrados. O *marca d'água* é uma lista de links para todas as exibições de Designer de XSD. Se o esquema tem erros, o seguinte texto é exibido no fim da lista: “Use Lista de erros para exibir e corrigir erros no conjunto.”  
  
## <a name="breadcrumb-bar"></a>Barra de rastreamento  
 A barra de rastreamento na parte inferior do modo de modelo de conteúdo mostra onde o nó selecionado é localizado no conjunto de esquema.  
  
## <a name="context-menus"></a>Menus de contexto  
 Quando você clica com o botão direito do mouse em um item na superfície de design ou no painel de espaço de trabalho, um menu de contexto aparece. A tabela a seguir descreve as opções que estão disponíveis para a superfície de design do modo de modelo de conteúdo.  
  
|Opção|Descrição|  
|------------|-----------------|  
|**Mostrar no XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|  
|**Mostrar na exibição de gráfico**|Alterna a O modo de gráfico.|  
|**Gerar XML de exemplo**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|  
|**Mostrar documentação**|Mostra ou de anotação/documentação de oculta conteúdo do nó.|  
|**Exporte diagrama como imagem...**|Salva a superfície de design para um arquivo XPS.|  
|**Modo de exibição de código**|Abre o arquivo que contém o nó selecionado no editor XML. O item selecionado em XML Schema Explorer também será selecionado no editor XML.|  
|**Janela Propriedades**|Abre o **propriedades** janela (se ainda não estiver aberto). Esta janela exibe informações sobre o nó.|  
  
 A tabela a seguir descreve as opções que estão disponíveis para o painel de espaço de trabalho.  
  
|Opção|Descrição|  
|------------|-----------------|  
|**Mostrar no XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|  
|**Mostrar na exibição de gráfico**|Alterna para representar graficamente a exibição.|  
|**Limpar o espaço de trabalho**|Limpa o espaço de trabalho e a superfície de design.|  
|**Remover do espaço de trabalho**|Removes selecionou nós de espaço de trabalho e da superfície de design.|  
|**Remova todos, exceto a seleção do espaço de trabalho**|Remove os nós que não são selecionados de espaço de trabalho e da superfície de design.|  
|**Gerar XML de exemplo**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|  
|**Selecionar tudo**|Selecionar todos os nós no painel de espaço de trabalho.|  
|**Modo de exibição de código**|Abre o arquivo que contém o nó selecionado no editor XML. O item selecionado em XML Schema Explorer também será selecionado no editor XML.|  
|**Janela Propriedades**|Abre o **propriedades** janela (se ainda não estiver aberto). Esta janela exibe informações sobre o nó.|  
  
## <a name="properties-window"></a>Janela Propriedades  
 Use o menu de contexto para abrir inicialmente o **propriedades** janela. Por padrão, o **propriedades** janela aparece no canto inferior direito do Visual Studio. Quando você clica em um nó que é renderizado no modo de exibição de modelo de conteúdo, as propriedades de nó serão exibidas no **propriedades** janela.  
  
## <a name="xsd-designer-toolbar"></a>Barra de ferramentas do designer XSD  
 Os seguintes botões da barra de ferramentas do designer XSD são ativados quando a exibição do modelo de conteúdo está ativo.  
  
 ![Ferramentas de Designer de esquema XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")  
  
|Opção|Descrição|  
|------------|-----------------|  
|**Mostrar o modo de início**|Alterna para o [Iniciar modo de exibição](../xml-tools/start-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **CTRL + 1**.|  
|**Mostrar exibição do modelo de conteúdo**|Alterna para o [exibição do modelo de conteúdo](../xml-tools/content-model-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **CTRL + 2**.|  
|**Mostrar exibição do gráfico**|Alterna para o [Graph exibição](../xml-tools/graph-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **CTRL + 3**.|  
|**Limpar o espaço de trabalho**|Limpa o espaço de trabalho e a superfície de design.|  
|**Remover do espaço de trabalho**|Removes selecionou nós de espaço de trabalho e serface de design.|  
|**Remova todos, exceto a seleção do espaço de trabalho**|Remove os nós que não são selecionados de espaço de trabalho e serface de design.|  
|**Mostrar documentação**|Mostra ou de anotação/documentação de oculta conteúdo do nó.|  
  
## <a name="panscroll"></a>Bandeja/rolagem  
 Você pode filtrar a superfície de design usando barras de rolagem ou mantendo a tecla CTRL quando você clique e arraste o mouse. Quando você filtra a superfície de design usando o clique e o arrastar, o cursor será alterado a quatro setas cruzadas apontando em quatro direções.  
  
## <a name="undoredo"></a>Desfazer/refazer  
 Desfazer/refaz o recurso é habilitado no modo de modelo de conteúdo para as seguintes ações:  
  
-   Adicionando um único nó arrastando e soltando-se.  
  
-   Adicionando mais nós da janela de resultados de pesquisa no esquema Explorer.  
  
-   Adicionando a exibição de nós do início.  
  
-   Excluindo única ou mais nós.  
  
## <a name="zoom"></a>Aplicar Zoom  
 O zoom está disponível no canto inferior direito da exibição do modelo de conteúdo.  
  
 O zoom pode ser controlado das seguintes maneiras:  
  
-   Mantendo a tecla CTRL e girar o mouse rode quando o mouse está sobre a superfície de exibição do modelo de conteúdo.  
  
-   Usando o controle deslizante. O controle deslizante mostra o nível atual de zoom.  
  
O controle deslizante de zoom é opaco ao selecionar, o passa sobre ele, ou utiliza o CTRL com a roda do mouse para aplicar zoom; em quaisquer outros vezes, é transparente.  
  
## <a name="xml-editor-integration"></a>Integração de editor XML  
 Você pode alternar para frente e para trás entre o designer XSD e o editor XML usando o menu de contexto.  
  
 Se você alterar o esquema definido no editor XML as alterações serão sincronizadas no modo de modelo de conteúdo. Para obter mais informações, consulte [integração com o Editor de XML](../xml-tools/integration-with-xml-editor.md).  
  
## <a name="see-also"></a>Consulte também  
 [O espaço de trabalho do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md)