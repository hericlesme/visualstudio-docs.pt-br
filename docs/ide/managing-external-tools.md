---
title: Gerenciar ferramentas externas | Microsoft Docs
ms.custom: 
ms.date: 11/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 78a3e1ee549a42681d6f15b432d0c6bb608976fd
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="manage-external-tools"></a>Gerenciar ferramentas externas

Você pode chamar ferramentas externas de dentro do Visual Studio usando o menu **Ferramentas**. Algumas ferramentas padrão estão disponíveis no menu **Ferramentas**, e você pode personalizar o menu adicionando outros executáveis de sua preferência.

## <a name="tools-available-on-the-tools-menu"></a>Ferramentas disponíveis no menu Ferramentas

O menu **Ferramentas** contém vários comandos internos, como:

* **Extensões e Atualizações** para [gerenciamento de Extensões do Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Gerenciador de Trechos de Código...** para [organizar Trechos de Código](code-snippets.md)
* **Proteção Preemptiva - Dotfuscator** para iniciar o [Dotfuscator Community Edition (CE)](dotfuscator/index.md) se ele estiver [instalado](dotfuscator/install.md)
* **Personalizar...** para [personalizar menus e barras de ferramentas](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opções...** para [configurar uma variedade de opções diferentes para o IDE do Visual Studio e outras ferramentas](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Adicionar novas ferramentas ao menu Ferramentas

É possível adicionar uma ferramenta externa para aparecer no menu **Ferramentas**.

1. Abra a caixa de diálogo **Ferramentas Externas**, escolhendo **Ferramentas** > **Ferramentas Externas...**.

1. Clique em **Adicionar** e preencha as informações. Por exemplo, a seguinte entrada faz com que o Windows Explorer abra o diretório do arquivo atualmente aberto no Visual Studio:

   * Título: `Open File Location`

   * Comando: `explorer.exe`

   * Argumentos: `/root, "$(ItemDir)"`

   ![Caixa de diálogo Ferramentas Externas](media/external-tools-dialog.png)

Esta é uma lista completa de argumentos que podem ser usados ao definir uma ferramenta externa:

|Nome|Argumento|Descrição|  
|----------|--------------|-----------------|  
|Caminho do item|$(ItemPath)|O nome de arquivo completo do arquivo atual (unidade + caminho + nome de arquivo).|  
|Diretório do item|$(ItemDir)|O diretório do arquivo atual (unidade + caminho).|  
|Nome de Arquivo do Item|$(ItemFilename)|O nome de arquivo do arquivo atual (nome de arquivo).|  
|Extensão de item|$(ItemExt)|A extensão de nome de arquivo do arquivo atual.|  
|Linha atual|$(CurLine)|A posição da linha atual do cursor na janela de código.|  
|Coluna atual|$(CurCol)|A posição da coluna atual do cursor na janela de código.|  
|Texto atual|$(CurText)|O texto selecionado.|  
|Caminho de destino|$(TargetPath)|O nome de arquivo completo do item a ser criado (unidade + caminho + nome de arquivo).|  
|Diretório de Destino|$(TargetDir)|O diretório do item a ser criado.|  
|Nome de Destino|$(TargetName)|O nome de arquivo do item a ser criado.|  
|Extensão de Destino|$(TargetExt)|A extensão de nome de arquivo do item a ser criada.|  
|Diretório binário|$(BinDir)|O local final do binário que está sendo criado (definido como unidade + caminho).|  
|Diretório do Projeto|$(ProjDir)|O diretório do projeto atual (unidade + caminho).|  
|Nome do arquivo de projeto|$(ProjFileName)|O nome de arquivo do projeto atual (unidade + caminho + nome de arquivo).|  
|Diretório da solução|$(SolutionDir)|O diretório da solução atual (unidade + caminho).|  
|Nome de arquivo da solução|$(SolutionFileName)|O nome de arquivo da solução atual (unidade + caminho + nome de arquivo).|

> [!NOTE]
> A barra de status do IDE exibe as variáveis Linha atual e Coluna atual para indicar a localização do ponto de inserção no Editor de Código ativo. A variável Texto atual retorna o texto ou o código selecionado nesse local.

## <a name="see-also"></a>Consulte também

[Ferramentas de build do C/C++](/cpp/build/reference/c-cpp-build-tools)
