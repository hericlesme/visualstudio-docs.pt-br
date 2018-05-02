---
title: AutoRecover, Caixa de diálogo Opções, Ambiente
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f6409e31a606fe31fa1296dc937616338f8d62c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="autorecover-environment-options-dialog-box"></a>AutoRecover, Caixa de diálogo Opções, Ambiente
Use essa página da caixa de diálogo Opções para especificar se os arquivos passam por backup automático ou não. Essa página também permite especificar se arquivos modificados são restaurados ou não quando o IDE (ambiente de desenvolvimento integrado) é desligado inesperadamente. Você pode acessar essa caixa de diálogo selecionando o menu **Ferramentas** e escolhendo **Opções** e, em seguida, selecionando a pasta **Ambiente** e a página **AutoRecuperação**. Se essa página não aparecer na lista, selecione **Mostrar todas as configurações** na caixa de diálogo **Opções**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

 **Salvar informações de AutoRecover a cada \<n> minutos** Use esta opção para personalizar a frequência em que um arquivo é salvo automaticamente no editor. Para arquivos salvos anteriormente, uma cópia do arquivo é salva em \\...\meus Documentos\Visual Studio \<*versão*>\Arquivos de Backup\\<*nome do projeto*>. Se o arquivo for novo e não tiver sido salvo manualmente, ele será salvo automaticamente usando um nome de arquivo gerado aleatoriamente.

 **Manter informações de AutoRecover por \<n> dias** Use esta opção para especificar quanto tempo o Visual Studio manterá os arquivos criados para recuperação automática.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Opções](../../ide/reference/options-dialog-box-visual-studio.md)