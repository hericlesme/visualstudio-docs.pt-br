---
title: GUIDs e IDs de comandos do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 44ae5ff7e9095d6c88d753342da30983b30b7364
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs e IDs de comandos do Visual Studio
Os valores GUID e a ID dos comandos incluídos no ambiente de desenvolvimento integrado (IDE) do Visual Studio são definidos em arquivos. VSCT que são instalados como parte do SDK do Visual Studio. Para obter mais informações, consulte [IDE-Defined comandos, Menus e grupos](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Para obter mais informações sobre como trabalhar com objetos IDE que são definidos em arquivos. VSCT, consulte [estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Localizando uma definição de comando  
 Como o Visual Studio define mais de mil comandos, não é prático para listá-los todos os aqui. Em vez disso, siga estas etapas para localizar a definição de um comando.  
  
#### <a name="to-locate-a-command-definition"></a>Para localizar uma definição de comando  
  
1.  No Visual Studio, abra os arquivos a seguir no *caminho de instalação do SDK do Visual Studio*pasta \VisualStudioIntegration\Common\Inc\: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     A maioria dos comandos do Visual Studio são definidos em SharedCmdDef.vsct e ShellCmdDef.vsct. VsDbgCmdUsed.vsct define comandos que pertencem ao depurador e Venusmenu.vsct define comandos que são específicos para desenvolvimento na Web.  
  
2.  Se o comando é um item de menu, observe o texto exato do item de menu. Se o comando é um botão da barra de ferramentas, observe o texto de dica de ferramenta que aparece quando você faz uma pausa nela.  
  
3.  Pressione CTRL + F para abrir o **localizar** caixa de diálogo.  
  
4.  No **localizar** , digite o texto que você anotou na etapa 2.  
  
5.  Verifique **todos os documentos abertos** é exibido no **examinar** caixa.  
  
6.  Clique o **Localizar próximo** botão até que o texto é selecionado no `<Strings>` seção um [elemento Button](../../extensibility/button-element.md).  
  
     O `<Button>` que o comando é exibido no elemento é a definição de comando.  
  
 Quando você encontrar a definição de comando, você pode colocar uma cópia do comando em outro menu ou barra de ferramentas, criando um [CommandPlacement elemento](../../extensibility/commandplacement-element.md) que tem o mesmo `guid` e `id` valores como o comando. Para obter mais informações, consulte [criando grupos reutilizável de botões](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Casos especiais  
 Nos casos a seguir, o texto do menu ou o texto de dica de ferramenta pode não corresponder exatamente o que está na definição de comando.  
  
-   Itens de menu que incluem um caractere de sublinhado, como o **impressão** comando o **arquivo** menu, em que o P é sublinhado.  
  
     Os caracteres são precedidas pelo caractere '&' em nomes de item de menu são exibidos como sublinhado. No entanto, os arquivos. VSCT são gravados em XML, que usa o caractere '&' para indicar os caracteres especiais e requer que um e comercial que deve ser exibidas deve ser escrito como&amp;'. Portanto, em um arquivo. VSCT, o **P**comando Imprimir aparece como '&amp;impressão '.  
  
-   Comandos que contêm texto dinâmico, como **salvar** *Filename atual*e gerado dinamicamente os itens de menu, como os itens no **arquivos recentes** lista.  
  
     Não há nenhuma maneira confiável para pesquisar texto dinâmico. Em vez disso, localizar um grupo que hospeda o comando desejado consultando [GUIDs e IDs do Visual Studio Menus](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [GUIDs e IDs do Visual Studio barras de ferramentas](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e procure a ID do grupo. Se a definição de comando não tem o grupo como seu [elemento pai](../../extensibility/parent-element.md), procure SharedCmdPlace.vsct e ShellCmdPlace.vsct (ou VsDbgCmdPlace.vsct para comandos do depurador) um `<CommandPlacement>` que define o pai do elemento de comando. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct, ShellCmdPlace.vsct, estão no *caminho de instalação do SDK do Visual Studio*\VisualStudioIntegration\Common\Inc\ pasta.  
  
## <a name="see-also"></a>Consulte também  
 [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referência do esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)