---
title: GUIDs e IDs de Menus do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 163f7b81295468a69cfb28959f608a21f94a4a99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134208"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUIDs e IDs de Menus do Visual Studio
Este tópico enumera os valores GUID e ID de menus e grupos na barra de menus do Visual Studio. Esses valores são definidos em arquivos. VSCT que são instalados como parte do SDK do Visual Studio. Para obter mais informações, consulte [IDE-Defined comandos, Menus e grupos](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Para obter mais informações sobre como trabalhar com objetos (IDE) do ambiente de desenvolvimento integrado que são definidos em arquivos. VSCT, consulte [estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
 Os menus e grupos na barra de menus do Visual Studio usam o GUID `guidSHLMainMenu`. No menu barra em si tem uma ID de `IDM_VS_TOOL_MAINMENU`.  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Grupos na barra de Menu do Visual Studio  
 Para adicionar um menu à barra de menus, defina um desses grupos como seu pai.  
  
|Grupo|ID|  
|-----------|--------|  
|Exibição/de edição de arquivo|IDG_VS_MM_FILEEDITVIEW|  
|Refatoração|IDG_VS_MM_REFACTORING:|  
|Projeto|IDG_VS_MM_PROJECT|  
|Build|IDG_VS_MM_BUILDDEBUGRUN|  
|Formato/ferramentas|IDG_VS_MM_TOOLSADDINS|  
|Comunidade/de ajuda de janela|IDG_VS_MM_WINDOWHELP|  
|Suplementos|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Menus na barra de Menu do Visual Studio  
 Para adicionar um grupo a um menu existente do Visual Studio, defina um dos menus a seguir como seu pai. Submenus não são incluídas nesta lista.  
  
|Menu|ID|  
|----------|--------|  
|Arquivo|IDM_VS_MENU_FILE|  
|Editar|IDM_VS_MENU_EDIT|  
|Exibir|IDM_VS_MENU_VIEW|  
|Refatoração|IDM_VS_MENU_REFACTORING|  
|Projeto|IDM_VS_MENU_PROJECT|  
|Build|IDM_VS_MENU_BUILD|  
|Formatar|IDM_VS_MENU_FORMAT|  
|Ferramentas|IDM_VS_MENU_TOOLS|  
|Janela|IDM_VS_MENU_WINDOW|  
|Suplementos|IDM_VS_MENU_ADDINS|  
|Comunidade|IDM_VS_MENU_COMMUNITY|  
|Ajuda|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Grupos de Menus do Visual Studio  
 As listas a seguir mostram os grupos que deriva diretamente da menus na barra de menus do Visual Studio. É a maneira mais rápida para adicionar um comando a um menu do Visual Studio definir um desses grupos como pai. Grupos que descendem do submenus não aparecem nesta seção.  
  
### <a name="file-menu-groups"></a>Grupos de Menu arquivo  
  
|Grupo|ID|  
|-----------|--------|  
|Novo/abrir|IDG_VS_FILE_FILE|  
|Adicionar|IDG_VS_FILE_ADD|  
|Solução|IDG_VS_FILE_SOLUTION|  
|Diversos|IDG_VS_FILE_MISC|  
|Salvar|IDG_VS_FILE_SAVE|  
|Renomear|IDG_VS_FILE_RENAME|  
|Navegador|IDG_VS_FILE_BROWSER|  
|Impressão|IDG_VS_FILE_PRINT|  
|Usado mais recentemente|IDG_VS_FILE_MRU|  
|Mover|IDG_VS_FILE_MOVE|  
|Sair|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>Editar grupos de Menu  
  
|Grupo|ID|  
|-----------|--------|  
|Desfazer/refazer|IDG_VS_EDIT_UNDOREDO|  
|Recortar/copiar/colar|IDG_VS_EDIT_CUTCOPY|  
|Selecionar|IDG_VS_EDIT_SELECT|  
|Ir para|IDG_VS_EDIT_GOTO|  
|Localizar|IDG_VS_EDIT_FIND|  
|Objetos|IDG_VS_EDIT_OBJECTS|  
|Verbos OLE|IDG_VS_EDIT_OLEVERBS|  
|Comando bem|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>Refatorar grupos de Menu  
  
|Grupo|ID|  
|-----------|--------|  
|Comuns|IDG_REFACTORING_COMMON|  
|Avançado|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>Exibir grupos de Menu  
  
|Grupo|ID|  
|-----------|--------|  
|Código de formulário|IDG_VS_VIEW_FORMCODE|  
|Navegador|IDG_VS_VIEW_BROWSER|  
|Definir modos de exibição|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|A arquitetura do Windows|IDG_VS_VIEW_ARCH_WINDOWS|  
|Organização Windows|IDG_VS_VIEW_ORG_WINDOWS|  
|Navegador de código|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|Windows de desenvolvimento|IDG_VS_VIEW_DEV_WINDOWS|  
|Barras de ferramentas|IDG_VS_VIEW_TOOLBARS|  
|Símbolos|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|Navegar|IDG_VS_VIEW_NAVIGATE|  
|Navegue pequena|IDG_VS_VIEW_SMALLNAVIGATE|  
|Pesquisador de Objetos|IDG_VS_VIEW_OBJBRWSR|  
|Comando bem|IDG_VS_VIEW_COMMANDWELL|  
|Páginas de propriedade|IDG_VS_VIEW_PROPPAGES|  
|Atualizar|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>Grupos de Menu do projeto  
  
|Grupo|ID|  
|-----------|--------|  
|Diversos adicionar|IDG_VS_PROJ_MISCADD|  
|Adicionar|IDG_VS_PROJ_ADD|  
|Pasta|IDG_VS_PROJ_FOLDER|  
|Unload/recarregar|IDG_VS_PROJ_UNLOADRELOAD|  
|Referência|IDG_VS_PROJ_REFERENCE|  
|Opções|IDG_VS_PROJ_OPTIONS|  
|Configurações|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>Criar grupos de Menu  
  
|Grupo|ID|  
|-----------|--------|  
|Solução|IDG_VS_BUILD_SOLUTION|  
|Seleção|IDG_VS_BUILD_SELECTION|  
|Otimização Guiada por Perfil|IDG_VS_PGO_SELECTION|  
|Diversos|IDG_VS_BUILD_MISC|  
|Cancelar|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>Grupos de Menu Ferramentas  
  
|Grupo|ID|  
|-----------|--------|  
|Linha de Comando|IDG_VS_TOOLS_CMDLINE|  
|Trechos de código|IDG_VS_TOOLS_SNIPPETS|  
|Subconjunto de objeto|IDG_VS_TOOLS_OBJSUBSET|  
|Opções|IDG_VS_TOOLS_OPTIONS|  
|Outras 2|IDG_VS_TOOLS_OTHER2|  
|Ferramentas externas|IDG_VS_TOOLS_EXT_TOOLS|  
|Personalizações externas|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>Grupos de Menu janela  
  
|Grupo|ID|  
|-----------|--------|  
|Novo|IDG_VS_WINDOW_NEW|  
|Encaixe/Close|IDG_VS_DOCKCLOSE|  
|Encaixe/ocultar|IDG_VS_DOCKHIDE|  
|Organizar|IDG_VS_WINDOW_ARRANGE|  
|Navegação|IDG_VS_WINDOW_NAVIGATION|  
|Lista|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>Grupos de Menu de ajuda  
  
|Grupo|ID|  
|-----------|--------|  
|Exemplos|IDG_VS_HELP_SAMPLES|  
|Suporte|IDG_VS_HELP_SUPPORT|  
|Sobre o|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Submenus de Menus do Visual Studio  
 A hierarquia a seguir mostra os submenus que estão associados com os menus na barra de menus do Visual Studio. Como apenas um grupo pode ter um menu como seu pai, cada submenu deve decrescem de um grupo em um menu, em vez de diretamente do menu. Para obter mais informações sobre a relação entre menus, grupos e submenus, consulte [adicionando um Submenu a um Menu](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Os nomes de menus na barra de menus do Visual Studio não são mostrados separadamente nesta hierarquia porque eles podem ser inferidos a convenção de nomenclatura para os grupos no IDE, da seguinte maneira: IDG_VS_*nome do Menu*_*nome do grupo*.  
  
|Grupo pai|Submenu|Grupos filho|  
|------------------|-------------|------------------|  
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|  
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|  
|||IDG_VS_FILE_OPENF_CASCADE|  
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|  
|||IDG_VS_FILE_ADD_PROJECT_EXI|  
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|  
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|  
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|  
|||IDG_VS_FILE_MOVE_PICKER|  
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|  
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|  
|||IDG_VS_WNDO_OTRWNDWS1... 6|  
|||IDG_VS_WNDO_WINDOWS2|  
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||  
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||  
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|  
|||IDG_VS_MNUDES_EDITNAMES|  
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|  
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|  
|||IDG_VS_BUILD_PROJPICKER|  
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|  
|||IDG_VS_REBUILD_PROJPICKER|  
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|  
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|  
|||IDG_VS_CLEAN_PROJPICKER|  
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|  
|||IDG_VS_DEPLOY_PROJPICKER|  
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|  
|||IDG_VS_PGO_BUILD_CASCADE_RUN|  
  
## <a name="see-also"></a>Consulte também  
 [GUIDs e IDs de barras de ferramentas do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUIDs e IDs de comandos do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)