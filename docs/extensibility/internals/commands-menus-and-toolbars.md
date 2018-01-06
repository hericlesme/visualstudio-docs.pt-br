---
title: Comandos, Menus e barras de ferramentas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa1513bcd61ac63fb9d2a59f69a8b2ce22cf5114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="commands-menus-and-toolbars"></a>Comandos, Menus e barras de ferramentas
Menus e barras de ferramentas são que os maneira como os usuários acessam comandos no seu VSPackage. Comandos são funções que realizar tarefas, como imprimir um documento, a atualização de uma exibição ou criar um novo arquivo. Menus e barras de ferramentas são maneiras gráficas convenientes para apresentar os comandos para os usuários. Normalmente, os comandos relacionados são agrupados juntos no mesmo menu ou barra de ferramentas.  
  
-   Menus normalmente são exibidos como cadeias de caracteres de uma palavra clusterizadas em uma linha na parte superior de uma janela de ferramenta ou o ambiente de desenvolvimento integrado (IDE). Menus também podem ser exibidos como resultado de um evento com o botão direito e são chamados de menus de atalho nesse contexto. Quando clicado, menus expanda para exibir um ou mais comandos. Comandos, quando clicado, podem realizar tarefas ou iniciar submenus que contêm comandos adicionais. Alguns nomes de menu conhecidas são arquivo, editar, exibir e janela. Para obter mais informações, consulte [estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
-   Barras de ferramentas geralmente são linhas de botões e outros controles, como caixas de combinação, caixas de listagem, caixas de texto e controladores de menu. Todos os controles de barra de ferramentas são associados a comandos. Quando você clica em um botão de barra de ferramentas, o comando associado está ativado. Botões da barra de ferramentas geralmente têm ícones que sugerem os comandos subjacentes, como uma impressora de um comando de impressão. Em um controle de lista suspensa, cada item na lista está associado um comando diferente. Um controlador de menu é um híbrido no qual um lado do controle é um botão de barra de ferramentas e o outro lado é uma seta para baixo que exibe comandos adicionais quando clicado. Para obter mais informações, consulte [adicionando um controlador de Menu a uma barra de ferramentas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Quando você criar um comando, você também deve criar um manipulador de eventos para ele. O manipulador de eventos determina quando o comando é visível ou habilitada, permite que você modifique seu texto e garante que o comando responde apropriadamente ("rotas") quando ativado. Na maioria dos casos, o IDE controla os comandos usando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Comandos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rota de uma maneira hierárquica, começando com o contexto do comando interno, com base na seleção de local e continuar para o contexto mais externo, com base na seleção global. Os comandos adicionados ao menu principal ficam imediatamente disponíveis para execução de scripts. Para obter mais informações, consulte [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) e [objetos de contexto da seleção](../../extensibility/internals/selection-context-objects.md).  
  
 Para definir novos menus e barras de ferramentas, você deve descrevê-los em um arquivo de tabela de comando do Visual Studio (. VSCT). Modelo de pacote do Visual Studio cria esse arquivo para você, juntamente com os elementos necessários para dar suporte a quaisquer comandos, barras de ferramentas e editores selecionados no modelo. Como alternativa, você pode escrever seu próprio arquivo. VSCT, usando o esquema xml descrito aqui: [referência de esquema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Para obter mais informações sobre como trabalhar com arquivos. VSCT, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Os tópicos nesta seção explicam como comandos, menus e barras de ferramentas funcionam no VSPackages.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Uma descrição detalhada da especificação de formato de tabela do comando.  
  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Descreve um compilador para tabelas de comando e sintaxe baseada em XML.  
  
 [Posicionamento padrão de comando, grupo e barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Descreve os comandos predefinidos, grupos, menus e barras de ferramentas.  
  
 [Comandos, menus e grupos definidos pelo IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Especifica o predefinidos de menus, comandos e grupos de comando disponíveis para uso pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Design de comando](../../extensibility/internals/command-design.md)  
 Explica como criar comandos.  
  
 [Otimizar os comandos de menu e da barra de ferramentas](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Fornece diretrizes para comandos.  
  
 [Disponibilização de comandos](../../extensibility/internals/making-commands-available.md)  
 Explica como fazer os comandos disponíveis para o Visual Studio.  
  
 [Comandos e menus que usam assemblies de interoperabilidade](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Explica como implementar os comandos que usam assemblies de interoperabilidade.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Explica o roteamento de comando VSPackages.