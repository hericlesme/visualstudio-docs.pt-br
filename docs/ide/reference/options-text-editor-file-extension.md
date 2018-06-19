---
title: Opções, Editor de Texto, Extensão de Arquivo
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.file_extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b5fc6249477cdab9a4c13608a260820a801e081
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945734"
---
# <a name="options-text-editor-file-extension"></a>Opções, Editor de Texto, Extensão de Arquivo
A caixa de diálogo Opções permite especificar como todos os arquivos com determinadas extensões de arquivo serão manipulados pelo IDE (ambiente de desenvolvimento integrado) do Visual Studio. Para cada **Extensão** que inserir, você pode selecionar uma Experiência de Edição. Isso permite escolher o editor ou o designer do IDE no qual os documentos de um determinado tipo serão abertos. Para exibir essas opções, escolha **Opções** no menu **Ferramentas**, expanda o nó **Editor de Texto** e selecione **Extensão de Arquivo**.

 Quando você selecionar uma opção "com codificação", uma caixa de diálogo será exibida sempre que você abrir um documento do tipo em questão que permitir selecionar um esquema de codificação para o documento. Isso pode ser útil se você estiver preparando versões dos documentos do projeto para uso em diferentes plataformas ou em diferentes linguagens de destino.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


## <a name="uielement-list"></a>Lista UIElement
 **Extensão**

 Digite a extensão de arquivo cuja Experiência de Edição no IDE você deseja definir.

 **Editor**

 Selecione o editor ou o designer do IDE em que documentos com essa extensão de arquivo serão abertos. Quando você selecionar uma opção "com codificação", uma caixa de diálogo será exibida sempre que você abrir um documento do tipo em questão que permitir selecionar um esquema de codificação.

 **Adicionar**

 Adiciona uma entrada que inclui a **Extensão** e a **Experiência de Edição** especificadas à Lista de extensões.

 **Removerr**

 Exclui a entrada selecionada da Lista de Extensões.

 **Lista de extensões**

 Lista todas as extensões para as quais uma Experiência de Edição foi especificada.

 **Mapear arquivos sem extensão para**

 Selecione esta opção se você quiser especificar como arquivos sem extensão serão tratados pelo IDE.

 **Opções de arquivos sem extensão**

 Fornece a mesma lista que o **Editor**. Selecione o editor ou o designer do IDE em que documentos sem extensão de arquivo serão abertos.

## <a name="see-also"></a>Consulte também

- [Como gerenciar modos do editor](../../ide/how-to-manage-editor-modes.md)