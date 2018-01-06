---
title: Comando Design | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fe3db0582c65a2ece2162ab24afb6d179b865a27
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="command-design"></a>Design de comando
Quando você adicionar um comando a um VSPackage, você deve especificar onde ele deve ser exibido quando ele está disponível e como ela será tratada.  
  
## <a name="defining-commands"></a>Definindo comandos  
 Para definir novos comandos, inclua um arquivo de tabela de comando do Visual Studio (. VSCT) em seu projeto VSPackage. Se você tiver criado um VSPackage usando o modelo de pacote do Visual Studio, o projeto inclui um desses arquivos. Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 O Visual Studio mescla todos os arquivos. VSCT encontrados para que ele pode exibir os comandos. Como esses arquivos são distintos quanto o VSPackage binário, o Visual Studio não tem que carregar o pacote para localizar os comandos. Para obter mais informações, consulte [como VSPackages adicionar elementos de Interface](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 O Visual Studio usa o <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> atributo de registro para definir recursos de menu e comandos. Para obter mais informações, consulte [implementação](../../extensibility/internals/command-implementation.md).  
  
 Comandos podem ser alterados em tempo de execução de várias maneiras diferentes. Eles podem ser exibidos ou ocultos, habilitados ou desabilitados. Eles podem exibir texto diferente ou ícones ou contêm valores diferentes. Uma grande quantidade de personalização pode ser executada antes que o Visual Studio carrega o VSPackage. Para obter mais informações, consulte [como VSPackages adicionar elementos de Interface](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Manipuladores de comandos  
 Quando você criar um comando, você deve fornecer um manipulador de eventos para executar o comando. Se o usuário seleciona o comando, ele deve ser roteado adequadamente. Roteamento de um comando significa enviá-la para o VSPackage correto para habilitar ou desabilitá-lo, ocultar ou exibi-lo e executá-lo se o usuário optar por fazê-lo. Para obter mais informações, consulte [roteamento algoritmo](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Ambiente de comando do Visual Studio  
 O Visual Studio pode hospedar qualquer número de VSPackages e cada uma pode contribuir seu próprio conjunto de comandos. O ambiente exibe somente os comandos que são apropriados para a tarefa atual. Para obter mais informações, consulte [disponibilidade](../../extensibility/internals/command-availability.md) e [objetos de contexto da seleção](../../extensibility/internals/selection-context-objects.md).  
  
 Um VSPackage que define novos comandos, menus, barras de ferramentas ou menus de atalho fornece as informações de comando para o Visual Studio no momento da instalação por meio de entradas do registro que fazem referência a recursos em assemblies nativos ou gerenciados. Cada recurso, em seguida, faz referência a um arquivo de recurso (.cto) de dados binários, que é gerado quando você compila um arquivo de tabela de comando do Visual Studio (. VSCT). Isso permite que o Visual Studio fornecer conjuntos de comandos mesclada, menus e barras de ferramentas sem precisar carregar cada VSPackage instalado.  
  
### <a name="command-organization"></a>Organização de comando  
 O ambiente posiciona comandos por grupo, prioridade e menu.  
  
-   Grupos são coleções lógicas de comandos relacionados, por exemplo, o **Recortar**, **cópia**, e **colar** grupo de comandos. Grupos são os comandos que aparecem nos menus.  
  
-   A prioridade determina a ordem na qual os comandos individuais em um grupo serão exibidos no menu.  
  
-   Menus atuam como contêineres para grupos.  
  
 O ambiente predefine alguns comandos, grupos e menus. Para obter mais informações, consulte [comando padrão, o grupo e o posicionamento da barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Um comando pode ser atribuído a um grupo primário. O grupo primário controla a posição do comando na estrutura do menu principal e no **personalizar** caixa de diálogo. Um comando pode aparecer em vários grupos; Por exemplo, um comando pode ser no menu principal, um menu de atalho e uma barra de ferramentas. Para obter mais informações, consulte [como VSPackages adicionar elementos de Interface](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Roteamento de comando  
 O processo de chamar e roteamento de comandos para VSPackages difere do processo de chamar métodos em instâncias de objeto.  
  
 O ambiente de rotas de comandos em sequência do contexto interno de comando (local), que é baseado na seleção atual, para o contexto mais externo de (global). O contexto primeiro que é capaz de executar o comando é o que o manipule. Para obter mais informações, consulte [roteamento algoritmo](../../extensibility/internals/command-routing-algorithm.md).  
  
 Na maioria dos casos, o ambiente controla os comandos usando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Como o esquema de roteamento de comando permite que vários objetos diferentes lidar com comandos, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pode ser implementada por qualquer número de objetos; eles incluem controles Microsoft ActiveX, implementações do modo de exibição de janela, objetos de documento, hierarquias de projeto e objetos de VSPackage (para comandos global). Em alguns casos especializados, por exemplo, roteamento comandos em uma hierarquia, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface deve ser implementada.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Implementação](../../extensibility/internals/command-implementation.md)|Descreve como implementar os comandos em um VSPackage.|  
|[Disponibilidade](../../extensibility/internals/command-availability.md)|Descreve como o contexto do Visual Studio determina quais comandos estão disponíveis.|  
|[Algoritmo de roteamento](../../extensibility/internals/command-routing-algorithm.md)|Descreve como a arquitetura de roteamento de comando do Visual Studio permite comandos sejam tratadas por diferentes VSPackages.|  
|[Diretrizes de posicionamento](../../extensibility/internals/command-placement-guidelines.md)|Sugere como posicionar comandos no ambiente do Visual Studio.|  
|[Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Descreve como VSPackages podem utilizar melhor a arquitetura de comando do Visual Studio.|  
|[Posicionamento padrão de comando, grupo e barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Descreve como VSPackages melhor pode usar os comandos que estão incluídos no Visual Studio.|  
|[Gerenciar VSPackages](../../extensibility/managing-vspackages.md)|Descreve como o Visual Studio carrega VSPackages.|  
|[Arquivos da tabela de comandos do Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fornece informações sobre arquivos. VSCT baseado em XML, que são usados para descrever o layout e a aparência de comandos no VSPackages.|