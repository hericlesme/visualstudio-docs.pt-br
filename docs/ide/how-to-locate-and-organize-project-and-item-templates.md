---
title: Organizar modelos no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 167ffa269ea8051a4791000d96a86cb5788af60d
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Como localizar e organizar modelos de projeto e de item

Os arquivos de modelo devem ser colocados em um local que o Visual Studio reconheça, para que os modelos apareçam nas caixas de diálogo **Novo Projeto** e **Adicionar Novo Item**. Você pode criar subcategorias personalizadas de modelos que também serão exibidas nas caixas de diálogo.

## <a name="locating-templates"></a>Localizando modelos

Os modelos instalados e os modelos do usuário são armazenados em dois locais diferentes. Se um arquivo compactado que inclui um arquivo .vstemplate existir nesses locais, o modelo aparecerá na caixa de diálogo **Novo Projeto** ou **Adicionar Novo Item**.

> [!TIP]
> Você pode definir o local dos modelos do usuário em **Ferramentas** > **Opções** > **Projetos e Soluções** > **Locais**.

### <a name="installed-templates"></a>Modelos instalados

Por padrão, os modelos instalados com o Visual Studio estão localizados em:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*Linguagem de Programação*\\*ID da Localidade*

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*Linguagem de Programação*\\*ID da Localidade*

Por exemplo, o diretório a seguir contém os modelos de item do Visual Basic para inglês (LCID 1033):

   C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="user-templates"></a>Modelos do usuário

Por padrão, os modelos do usuário estão localizados em:

- %USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates

- %USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates

Por exemplo, o seguinte diretório contém modelos de projeto do usuário para C#:

   C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#\

> [!NOTE]
> O local do modelo de usuário não inclui subpastas de localidade para modelos localizados.

Você pode alterar o diretório padrão dos modelos do usuário na caixa de diálogo **Opções** em **Projetos e Soluções** > **Locais**.

## <a name="organizing-templates"></a>Organizando modelos

As categorias nas caixas de diálogo **Novo Projeto** e **Adicionar Novo Item** refletem as estruturas de diretório que existem nos locais dos modelos instalados e dos modelos do usuário. É possível modificar essas estruturas de diretório para organizar seus modelos de forma que faça sentido para você.

> [!NOTE]
> Você não pode criar uma nova categoria no nível da linguagem de programação. Novas categorias podem ser criadas apenas dentro de cada linguagem.

> [!NOTE]
> Se as estruturas de diretório para os modelos instalados e os modelos do usuário de um idioma específico não forem as mesmas (ou seja, se houver diretórios em uma pasta, mas não em outra), todas as categorias serão mostradas na caixa de diálogo **Novo Projeto**.

### <a name="organizing-user-templates"></a>Organizando modelos do usuário

Modelos do usuário podem ser organizados em suas próprias categorias adicionando novas pastas ao local do modelo do usuário. A caixa de diálogo **Novo Projeto** reflete alterações feitas nas categorias de modelo.

#### <a name="to-create-new-user-project-template-categories"></a>Para criar novas categorias de modelo de projeto do usuário

1. Crie uma pasta na pasta de linguagem de programação no diretório de modelo de projeto do usuário. Por exemplo, para estabelecer uma categoria **HelloWorld** para modelos de projeto C#, crie o seguinte diretório:

    \%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld\

1. Coloque todos os modelos dessa categoria na nova pasta.

1. No menu **Arquivo**, escolha **Novo** > **Projeto**.

   A categoria **HelloWorld** aparece na caixa de diálogo **Novo Projeto** em **Instalado** > **Visual C#**.

#### <a name="to-create-new-user-item-template-categories"></a>Para criar novas categorias de modelo de item do usuário

1. Crie uma pasta na pasta de linguagem de programação no diretório de modelo de item do usuário. Por exemplo, para estabelecer uma categoria **HelloWorld** para modelos de item C#, crie o seguinte diretório:

    \%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld\

1. Coloque todos os modelos dessa categoria na nova pasta.

1. Crie um projeto ou abra um projeto existente. Em seguida, no menu **Projeto**, escolha **Adicionar Novo Item**.

   A categoria **HelloWorld** aparece na caixa de diálogo **Adicionar Novo Item** em **Instalado** > **Itens do Visual C#**.

### <a name="displaying-templates-in-parent-categories"></a>Exibindo modelos em categorias pai

Você pode habilitar modelos em subcategorias a serem exibidos em suas categorias pai usando o elemento `NumberOfParentCategoriesToRollUp` no arquivo .vstemplate. Essas etapas são idênticas para modelos de projeto e modelos de item.

#### <a name="to-display-templates-in-parent-categories"></a>Para exibir modelos em categorias pai

1. Localize o arquivo .zip que contém o modelo.

1. Extraia o arquivo .zip.

1. Abra o arquivo .vstemplate no Visual Studio.

1. No elemento `TemplateData`, adicione um elemento `NumberOfParentCategoriesToRollUp`. Por exemplo, o código a seguir torna o modelo visível na categoria pai, mas não superior.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Salve e feche o arquivo .vstemplate.

1. Selecione os arquivos em seu modelo, clique com o botão direito do mouse na seleção e escolha **Enviar para** > **Pasta compactada (zipada)**.

   Os arquivos são compactados em um arquivo .zip.

1. Exclua os arquivos de modelo extraídos e o arquivo .zip de modelo antigo.

1. Coloque o novo arquivo .zip no diretório que tinha o arquivo .zip excluído.

## <a name="see-also"></a>Consulte também

[Personalizando modelos](../ide/customizing-project-and-item-templates.md)  
[Referência de esquema de modelo do Visual Studio (extensibilidade)](../extensibility/visual-studio-template-schema-reference.md)  
[NumberOfParentCategoriesToRollUp (Modelos do Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)  
[Como criar modelos de projeto](../ide/how-to-create-project-templates.md)  
[Como criar modelos de item](../ide/how-to-create-item-templates.md)
