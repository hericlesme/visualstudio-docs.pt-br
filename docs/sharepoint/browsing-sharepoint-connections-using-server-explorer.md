---
title: Conexões do SharePoint usando o Gerenciador de servidores de navegação | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5631699f324451034d0d5c66161c004c793add37
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691411"
---
# <a name="browsing-sharepoint-connections-that-use-server-explorer"></a>Pesquisa de conexões do SharePoint que usam o Gerenciador de servidores
  Agora você pode procurar conexões locais do SharePoint no **Server Explorer**. Usando essa técnica, você pode navegar por meio dos componentes de um site do SharePoint em seu sistema. Componentes do site do SharePoint, como definições de listas e tipos de conteúdo, aparecem em um nó chamado **conexões do SharePoint** na exibição de árvore de **Server Explorer**. Para exibir **Server Explorer**, na barra de menus, escolha **exibição**, **Server Explorer**. Além de exibir os componentes do site do SharePoint, você pode remover itens, exibir suas propriedades ou atualizar a exibição de árvore usando comandos no menu de atalho.  
  
> [!IMPORTANT]  
>  Para procurar um site do SharePoint, você deve ser um administrador do conjunto de sites do SharePoint, e você deve estar executando o Visual Studio como administrador do computador local. Caso contrário, o site será exibido na **Server Explorer**, mas você não pode expandir o nó. Para verificar se você for um administrador do conjunto de sites, abra o site em um navegador da web, abra o **ações do Site** menu, escolha **permissões de Site**e, em seguida, o **permissões: Team Site** página, escolha o **administradores** comando o **gerenciar** grupo na faixa de opções. O nome será exibido na caixa de texto se você for um administrador de conjunto de sites. Se o **administradores** comando não aparece no grupo de gerenciamento na faixa de opções, você não é um administrador do conjunto de sites e você deve obter as permissões apropriadas do administrador do site.  
  
## <a name="server-explorer-nodes"></a>Nós do Gerenciador de servidores
 Cada componente de um site do SharePoint é representado por um nó no **Server Explorer** em modo de exibição de árvore **conexões do SharePoint**. Por exemplo, sites do SharePoint padrão incluem um tipo de conteúdo chamado discussão, que representa um tipo de discussão que exibe o **discussões** página do site do SharePoint. O tipo de conteúdo de discussão contém vários campos. Para exibir esses campos em **Server Explorer**, expanda o **ContentTypes** nó e, em seguida, o **discussão** nó. Em tem vários nós de campo, como título, discussão assunto e corpo.  
  
## <a name="node-shortcut-menu-commands"></a>Comandos de menu de atalho do nó
 Cada nó tem um menu de atalho que você pode acessar clicando duas vezes no nó ou selecioná-la e, em seguida, escolher o **Shift**+**F10** chaves. Comandos de nó podem incluir o seguinte:  
  
|Nome do comando|Descrição|  
|------------------|-----------------|  
|Atualizar|Atualiza a exibição de árvore para refletir as alterações que possam ter ocorrido desde a última vez em que o nó foi exibido.|  
|Excluir|Remove o nó selecionado na exibição de árvore. **Observação:** este comando só está habilitado em conexões do SharePoint listados sob o **conexões do SharePoint** nó.|  
|Propriedades|Exibe as propriedades disponíveis para o nó selecionado no **propriedades** janela. As propriedades são todos somente leitura e não em cada nó tem propriedades associadas a ele.|  
|Adicionar Conexão|Permite que você especifique um site do SharePoint que você deseja procurar. Disponível no **conexões do SharePoint** nó e nós subsite.|  
|Exibir no navegador|Exibe a lista selecionada no navegador da Web. Este comando está disponível em algumas listas sob o **lista** nó que está contida no **listas e bibliotecas**.|  
  
## <a name="related-topics"></a>Tópicos relacionados
  
|Título|Descrição|  
|-----------|-----------------|  
|[Como adicionar ou remover conexões do SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Descreve as etapas necessárias para adicionar um novo site do SharePoint para o **conexões do SharePoint** nó **Server Explorer**.|  
  
## <a name="see-also"></a>Consulte também
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 