---
title: Caixa de diálogo Geral, Ambientes, Opções
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f12249cc8d0e8bd8396e1e1ebbbfefeddbb22b60
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="general-environment-options-dialog-box"></a>Caixa de diálogo Geral, Ambientes, Opções

Use esta página para alterar temas de cores, configurações de barra de status e associações de extensões de arquivo, entre outras coisas, para o IDE (ambiente de desenvolvimento integrado). Você pode acessar a caixa de diálogo **Opções** abrindo o menu **Ferramentas**, escolhendo **Opções**, abrindo a pasta **Ambiente** e, em seguida, escolhendo a página **Geral**. Se essa página não aparecer na lista, marque a caixa de seleção **Mostrar todas as configurações** na caixa de diálogo **Opções**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, abra o menu **Ferramentas** e escolha **Importar e Exportar Configurações**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="visual-experience"></a>Experiência visual

**Tema da cor**

Escolha o tema de cor **Azul**, **Claro** ou **Escuro** para o IDE.

É possível instalar temas predefinidos adicionais e criar temas personalizados, baixando e instalando o **Visual Studio Color Theme Editor** do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Após você instalar essa ferramenta, temas de cores adicionais aparecem na caixa de listagem Tema da cor.

**Aplicar a capitalização de título à barra de menus**

Menus têm a **Capitalização de título** por padrão. Desmarque essa opção para defini-los como **TODAS EM MAIÚSCULAS**.

**Ajustar autom. a experiência visual com base no desempenho do cliente**

Especifica se o Visual Studio ajusta automaticamente a experiência visual ou se você a ajusta de maneira explícita. Esse ajuste pode alterar a exibição de cores de gradientes para cores simples ou pode restringir o uso de animações em menus ou janelas pop-up.

**Habilitar experiência avançada do cliente**

Habilita a experiência visual completa do Visual Studio, incluindo animações e gradientes. Desmarque esta opção quando estiver usando conexões da Área de Trabalho Remota ou adaptadores de gráficos mais antigos, uma vez que esses recursos podem ter um desempenho ruim nesses casos. Essa opção fica disponível somente quando você desmarca a opção **Ajustar autom. a experiência visual com base no desempenho do cliente**.

**Usar aceleração de elementos gráficos de hardware se disponível**

Usa aceleração de elementos gráficos de hardware se estiver disponível, em vez de aceleração de software.

## <a name="other"></a>Outros

**Itens mostrados no menu Janela**

Personaliza o número de janelas que aparecem na lista Janelas do menu **Janela**. Digite um número entre 1 e 24. Por padrão, o número é 10.

**Itens mostrados em listas usadas recentemente**

Personaliza o número de projetos e arquivos usados mais recentemente que aparecem no menu **Arquivo**. Digite um número entre 1 e 24. Por padrão, o número é 10. Esta é uma maneira fácil de recuperar projetos e arquivos usados recentemente.

**Mostrar barra de status**

Exibe a barra de status. A barra de status fica localizada na parte inferior da janela do IDE e exibe informações sobre o progresso das operações em andamento.

**Botão Fechar afeta apenas a janela da ferramenta ativa**

Especifica que, quando o botão **Fechar** é acionado, somente a janela da ferramenta que está em foco é fechada, e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, essa opção é selecionada.

**Botão Ocultar Automaticamente afeta apenas a janela da ferramenta ativa**

Especifica que, quando o botão **Ocultar Automaticamente** é acionado, somente a janela da ferramenta que está em foco é ocultada automaticamente, e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, essa opção não é selecionada.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Opções do Ambiente](../../ide/reference/environment-options-dialog-box.md)
- [Personalizando layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md)