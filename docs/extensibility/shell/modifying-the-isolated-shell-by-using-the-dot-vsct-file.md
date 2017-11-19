---
title: Modificando o Shell isolado usando o. Arquivo VSCT | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fcdaab4c5c9f0ee5522ae372e4a0cd94fb113eed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modificando o Shell isolado usando o. Arquivo VSCT
O projeto de interface do usuário para um projeto do Visual Studio shell isolado contém um arquivo. VSCT que permite que você especifique quais grupos de aplicativos e comandos individuais estão disponíveis no aplicativo. A seguir está um trecho de um arquivo. VSCT não modificado.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Por padrão, a maioria dos comandos e grupos de comando são incluídos. Para excluir um comando ou um grupo de comandos, simplesmente remova esse comando ou grupo.  
  
 Por exemplo, para remover o próximo painel e os comandos anteriores do painel, descomente o `No_PaneNextPaneCommand` e `No_PanePrevPaneCommand` entradas:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Para uma mais detalhada exemplo essas personalizações, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Arquivos de referência  
 O arquivo. VSCT de padrão para um aplicativo referencia os arquivos a seguir. Esses arquivos estão localizados no subdiretório \VisualStudioIntegration\Common\Inc\ do diretório de instalação do SDK do Visual Studio.  
  
|Arquivo|Descrição|  
|----------|-----------------|  
|wbids.h|Identidades de interface do usuário para o pacote da Web procurar.|  
|AppIDCmdUsed.vsct|Tabela de comando para os principais elementos de interface de usuário do Visual Studio.|  
|EmulatorCmdUsed.vsct|Tabela de comando para elementos de interface do usuário de emulação editor Emacs e resumo.|  
|Vsdebugguids.h|Define os GUIDs dos comandos, página de opções e outros recursos do depurador do Visual Studio.|  
|VsDbgCmdUsed.vsct|Tabela de comando do depurador.|  
  
 O arquivo de AppIDCmdUsed.vsct inclui elementos de interface de usuário do Visual Studio com base em símbolos definidos no arquivo. VSCT do aplicativo.  
  
 Para obter mais informações, consulte [criar tabela de comando XML (. Arquivos VSCT)](../internals/designing-xml-command-table-dot-vsct-files.md) e [referência de esquema XML do VSCT](../vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Consulte também  
 [Shell isolado do Visual Studio](visual-studio-isolated-shell.md)