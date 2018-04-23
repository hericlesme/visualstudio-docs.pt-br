---
title: Elemento de sinalizador de comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 036b9658957b76b62e3a9b44b59e07700f276a32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="command-flag-element"></a>Elemento de sinalizador de comando
Modifica seu elemento pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 A seção a seguir descreve os valores de elemento válido.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Valor|Descrição|  
|-----------|-----------------|  
|AllowParams|Indica que os usuários podem inserir parâmetros de comando na **comando** janela quando eles digitar o nome canônico do comando.<br /><br /> Válida para: `Button`|  
|AlwaysCreate|Menu é criado, mesmo se ele não tiver grupos ou botões.<br /><br /> Válida para: `Menu`|  
|CaseSensitive|Entradas de usuário diferenciam maiusculas de minúsculas.<br /><br /> Válida para: `Combo`|  
|CommandWellOnly|Aplica esse sinalizador, se o comando não aparecer no menu de nível superior e você deseja torná-lo disponível para personalização adicional de shell, por exemplo, para associação a um atalho de teclado. Depois que o VSPackage estiver instalado, você pode personalizar esses comandos abrindo o **opções** caixa de diálogo e, em seguida, editando o posicionamento de comando na **teclado ambiente** categoria. Este sinalizador não afeta o posicionamento em menus de atalho, barras de ferramentas, controladores de menu ou submenus.<br /><br /> Válido para: `Button`, `Combo`|  
|DefaultDisabled|Por padrão, o comando será desabilitado se o VSPackage que implementa não está carregado ou o `QueryStatus` método não foi chamado.<br /><br /> Válido para: `Button`, `Combo`|  
|DefaultDocked|Encaixado por padrão. Essa configuração não se aplica a barras de ferramentas, porque sempre são encaixados.|  
|DefaultInvisible|Por padrão, o comando é invisível se o VSPackage que implementa não está carregado ou o `QueryStatus` método não foi chamado.<br /><br /> É recomendável que você combinar isso com o `DynamicVisibility` sinalizador.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|  
|DontCache|O ambiente de desenvolvimento não armazena em cache o `QueryStatus` resultados do método para este comando.<br /><br /> Para um menu, isso indica que um controlador de menu não armazenar em cache o texto de seus itens de menu. Use este sinalizador quando o menu contém itens dinâmicos ou itens que tenham texto dinâmico.<br /><br /> Válido para: `Button`, `Menu`|  
|DynamicItemStart|Indica o início de uma lista dinâmica. Isso permite que o ambiente criar uma lista sucessivamente chamando o `QueryStatus` método em itens de lista até que o sinalizador OLECMDERR_E_UNSUPPORTED é retornado. Isso funciona bem para itens, como os usados mais recentemente (MRU) listas e listas de janelas.<br /><br /> Válida para: `Button`|  
|DynamicVisibility|A visibilidade do comando pode ser alterada por meio de `QueryStatus` método ou por meio de um GUID que é incluído no contexto de `VisibilityConstraints` seção.<br /><br /> Aplica-se aos comandos que aparecem nos menus e barras de ferramentas de janela de ferramenta, mas não em barras de ferramentas de nível superior que aparecem na janela principal. Itens de nível superior da barra de ferramentas podem ser desabilitados, mas não ocultos, quando o sinalizador OLECMDF_INVISIBLE é retornado do `QueryStatus` método. Comandos da barra de ferramentas que aparecem na barra de ferramentas de janela de ferramenta podem ser ocultados.<br /><br /> Em um menu, esse sinalizador também indica que ele deve ser automaticamente ocultado quando todos os seus membros estão ocultos. Esse sinalizador é geralmente atribuído aos submenus porque menus de nível superior já tem esse comportamento.<br /><br /> Esse sinalizador deve ser combinado com o `DefaultInvisible` sinalizador.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|  
|Teclas de filtragem|Consulte o tópico de filtragem de chaves em [combinação elemento](../extensibility/combo-element.md).<br /><br /> Válida para: `Combo`|  
|FixMenuController|Se esse comando é posicionado em um controlador de menu, o comando sempre é o padrão. Isto é, o comando é selecionado sempre que o botão do controlador de menu em si é selecionado. Se o controlador de menu tem o `TextIsAnchorCommand` o sinalizador será definido, em seguida, o controlador de menu também usa o texto do comando que tenha o `FixMenuController` sinalizador.<br /><br /> Apenas um comando em um controlador de menu deve ter o `FixMenuController` sinalizador. Se mais de um comando é marcado assim, o último comando no menu torna-se o comando padrão.<br /><br /> Válida para: `Button`|  
|IconAndText|Mostre um ícone e o texto no menu e barra de ferramentas.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|O recurso de preenchimento automático está desativado.<br /><br /> Válida para: `Combo`|  
|NoButtonCustomize|Não permitir que o usuário personalize este botão.<br /><br /> Válido para: `Button`, `Combo`|  
|NoKeyCustomize|Não habilite a personalização de teclado.<br /><br /> Válido para: `Button`, `Combo`|  
|NoShowOnMenuController|Se esse comando é posicionado em um controlador de menu, o comando não aparecer na lista suspensa.<br /><br /> Válida para: `Button`|  
|NotInTBList|Não aparecer na lista de barras de ferramentas disponíveis. Isso é válido somente para tipos de menu da barra de ferramentas.<br /><br /> Válida para: `Menu`|  
|NoToolbarClose|Usuário não é possível fechar a barra de ferramentas. Isso é válido somente para tipos de menu da barra de ferramentas.<br /><br /> Válida para: `Menu`|  
|PICT|Mostre somente um ícone em uma barra de ferramentas, mas apenas o texto em um menu. Se nenhum ícone for especificado, mostra um espaço em branco que pode ser clicado em uma barra de ferramentas.<br /><br /> Válida para: `Button`|  
|PostExec|Faz com que o comando sem bloqueio. O ambiente de desenvolvimento adia a execução até que todas as consultas de pré-processando sejam concluídas.<br /><br /> Válida para: `Button`|  
|RouteToDocs|O comando é roteado para o documento ativo.<br /><br /> Válida para: `Button`|  
|StretchHorizontally|Quando esse sinalizador é definido, a largura torna-se a largura mínima da caixa de combinação e se há espaço na barra de ferramentas, caixa de combinação expande para preencher o espaço disponível. Isso ocorre somente se a barra de ferramentas horizontal está encaixada e apenas uma caixa de combinação na barra de ferramentas pode usar o sinalizador (o sinalizador será ignorado em todas, exceto a primeira caixa de combinação).<br /><br /> Válida para: `Combo`|  
|TextMenuUseButton|Use o `ButtonText` campo menus. O campo padrão é `MenuText` se for especificado.<br /><br /> Válida para: `Button`|  
|TextoAltera|O texto de comando ou menu pode ser alterado em tempo de execução, normalmente por meio de `QueryStatus` método.<br /><br /> Válido para: `Button`, `Menu`|  
|TextChangesButton|Válida para: `Button`|  
|TextIsAnchorCommand|Para um controlador de menu, o texto do menu é obtido do comando padrão (âncora). Um comando de âncora é o último comando selecionado ou travada. Se este sinalizador não for definido, o controlador de menu usa seu próprio `MenuText` campo. No entanto, clicando em controlador de menu ainda permite que o último comando selecionado desse controlador de.<br /><br /> Recomendamos que você combine esse sinalizador com a `TextChanges` sinalizador.<br /><br /> Esse sinalizador aplica-se somente a menus do tipo MenuController ou MenuControllerLatched.<br /><br /> Válida para: `Menu`|  
|TextMenuCtrlUseMenu|Use o `MenuText` campo em controladores de menu. O campo padrão é `ButtonText`.<br /><br /> Válida para: `Button`|  
|TextMenuUseButton|Use o `ButtonText` campo menus. O campo padrão é `MenuText` se for especificado.<br /><br /> Válida para: `Button`|  
|TextOnly|Mostra apenas o texto em uma barra de ferramentas ou um menu, mas nenhum ícone mesmo se o ícone for especificado.<br /><br /> Válida para: `Button`|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Fornece um grupo para [elemento Button](../extensibility/button-element.md) elementos.|  
|[Elemento Menus](../extensibility/menus-element.md)|Define todos os menus que implementa um VSPackage.|  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)