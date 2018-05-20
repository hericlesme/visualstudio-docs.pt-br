---
title: EditorConfig
description: Usando um arquivo editorconfig para habilitar estilos de codificação de projeto consistentes no Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 336ec5ef0779bcd67302bea7b51851dced531a7d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Criando e editando um arquivo EditorConfig personalizado

No Visual Studio para Mac, você pode adicionar um arquivo [EditorConfig](http://editorconfig.org/) ao seu projeto ou base de código para impor estilos de codificação consistente para todas as pessoas que trabalham na base de código. As configurações declaradas no arquivo EditorConfig têm precedência sobre as configurações do editor de texto globais do Visual Studio. Usar EditorConfig dentro de seu projeto ou base de código permite que você defina o estilo de codificação, as preferências e os avisos para seu projeto. Isso torna mais fácil para todos os usuários do Visual Studio para Mac aderirem às práticas de codificação de um projeto.

Arquivos [EditorConfig](http://editorconfig.org/) são compatíveis com muitos editores de código e IDEs, incluindo o Visual Studio 2017. 

## <a name="supported-settings"></a>Configurações com suporte

O editor no Visual Studio é compatível com o conjunto principal de [propriedades do EditorConfig](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig também dá suporte à [Formatação de estilo de código](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) em C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Adicionar um arquivo EditorConfig a um projeto

### <a name="adding-a-new-editorconfig-file"></a>Adicionando um novo arquivo EditorConfig

1. Abra seu projeto no Visual Studio para Mac. Selecione o nó do projeto ao qual deseja adicionar arquivos.

2. Com o nó do projeto selecionado, vá até **Arquivo > Novo Arquivo…** na barra de menus para abrir a caixa de diálogo **Novo Arquivo**.

3. Escolha **Diversos > Arquivo de Texto Vazio** e dê a ele um **Nome** `.editorconfig`. Pressione **Novo** para criar o arquivo e abri-lo no editor:

    ![Caixa de diálogo Novo Arquivo](media/editorconfig-image1.png)

4. Edite o arquivo. Por exemplo:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Adicionar o arquivo não atualiza automaticamente as configurações. Para refletir as configurações do arquivo `.editorconfig`, selecione o nó do projeto e escolha **Editar > Formatar > Formatar Documento** na barra de menus:

    ![Item de menu Formatar Documento](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Adicionando um arquivo EditorConfig existente

Se estiver trabalhando com um projeto ou solução que já contém um arquivo `.editorconfig`, você não precisará fazer para aplicar as configurações. Novas linhas de código serão formatadas de acordo com as configurações de EditorConfig. Observe que, enquanto o Visual Studio para Mac respeita arquivos `.editorconfig` no nível da solução, eles podem não aparecer no Painel de Soluções porque arquivos que começam com `.` são arquivos ocultos no macOS.

Talvez você queira reutilizar um arquivo `.editorconfig` existente em seu projeto. Para adicionar um arquivo existente, primeiro você precisará exibir arquivos ocultos no Localizador digitando o seguinte comando no **Terminal**:

```bash
$ defaults write com.apple.Finder AppleShowAllFiles true
$ killall Finder
```

Quando o arquivo `.editorconfig` estiver visível, arraste-o para o nó do projeto. Quando vir a seguinte caixa de diálogo, selecione a opção **Copiar o arquivo para o diretório** e selecione **OK**:

![Item de menu Formatar Documento](media/editorconfig-image3.png)

Para refletir as configurações do arquivo `.editorconfig`, selecione o nó do projeto e escolha **Editar > Formatar > Formatar Documento** na barra de menus.

## <a name="editing-an-editorconfig-file"></a>Editando um arquivo EditorConfig

Os arquivos EditorConfig usam um layout de arquivo simples para especificar as configurações, que é explicado abaixo usando um exemplo anterior:


```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Definir `root` como `true` sinalizará este arquivo como o arquivo principal da base de código e arquivos `.editorconfig` superiores no projeto serão ignorados, conforme explicado na seção [Substituir configurações de EditorConfig](#override-editorconfig-settings).

Cada seção é indicada por chaves (**[ ]**) e especifica informações sobre os tipos de arquivos a que as propriedades seguintes devem se referir.

No exemplo acima, algumas configurações são aplicadas a todos os arquivos no projeto e outras são adicionadas apenas a arquivos C#. As capturas de tela abaixo mostram antes e depois de as configurações `.editorconfig` serem aplicadas:

**Antes**:

![Antes das configurações de editorconfig serem aplicadas](media/editorconfig-image4.png)

**Depois**:

![após as configurações de editorconfig serem aplicadas](media/editorconfig-image5.png)

Para obter mais informações sobre as configurações de EditorConfig disponíveis, consulte o artigo [Configurações de convenção de codificação do .NET para o EditorConfig](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) e a seção [Propriedades com suporte](http://editorconfig.org/#supported-properties) na documentação oficial.

## <a name="override-editorconfig-settings"></a>Substituir as configurações de EditorConfig

É possível ter mais de um arquivo `.editorconfig` em cada solução. O Visual Studio para Mac lê arquivos `.editorconfig` de cima para baixo na solução, adicionando e substituindo configurações conforme faz isso. Isso significa que as configurações de `.editorconfig` _mais próximas_ do arquivo que você está editando terão precedência. 

Se você quiser garantir que _nenhuma_ configuração de nenhum arquivo `.editorconfig` de nível superior seja aplicada a essa parte da base de código, adicione a propriedade `root=true` ao topo do arquivo `.editorconfig` de nível inferior:

```EditorConfig
# top-most EditorConfig file
root = true
```