---
title: "Usando as configurações do EditorConfig no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.workload: multiple
ms.openlocfilehash: 0219ff704e22ab1c27d47e312825a66cb3a15166
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Criar configurações do editor portátil e personalizado com o EditorConfig

No Visual Studio de 2017, você pode adicionar um arquivo [EditorConfig](http://editorconfig.org/) ao seu projeto ou base de código para impor estilos de codificação consistente para todas as pessoas que trabalham na base de código. As configurações de EditorConfig têm precedência sobre as configurações do editor de texto global do Visual Studio. Isso significa que é possível personalizar cada base de código para usar as configurações de editor de texto específicas para esse projeto. Você ainda pode definir suas preferências pessoais editor na caixa de diálogo **Opções** do Visual Studio. Essas configurações serão aplicadas sempre que você estiver trabalhando em uma base de código sem um arquivo .editorconfig ou quando o arquivo .editorconfig não substituir determinada configuração. Um exemplo de como essa preferência é o estilo de recuo&mdash;tabulações ou espaços.

As configurações do EditorConfig são compatíveis com vários editores de códigos e IDEs, incluindo o Visual Studio. Ele é um componente portátil que acompanha o seu código e pode impor estilos de codificação mesmo fora do Visual Studio.

## <a name="coding-consistency"></a>Consistência de codificação

As configurações em arquivos EditorConfig permitem manter configurações e estilos de codificação consistentes em uma base de código, como estilo de recuo, largura de tabulação, caracteres de fim de linha, codificação e mais, independentemente do editor ou IDE usado. Por exemplo, ao codificar em C#, se sua base de código tem uma convenção de preferir que os recuos sempre sejam compostos por cinco caracteres de espaço, que os documentos usem codificação UTF-8 e que cada linha sempre termine com uma CR/LF, é possível configurar um arquivo .editorconfig para fazer isso.

As convenções de codificação usadas em seus projetos pessoais podem ser diferentes das usadas nos projetos da sua equipe. Por exemplo, talvez você prefira que, quando estiver codificando, o recuo adicione um caractere de tabulação. No entanto, sua equipe pode preferir que o recuo adicione quatro caracteres de espaço em vez de um caractere de tabulação. Os arquivos EditorConfig resolvem esse problema permitindo que você tenha uma configuração para cada cenário.

Como as configurações estão contidas em um arquivo na base de código, elas viajam juntamente com essa base de código. Contanto que você abra o arquivo de código em um editor em conformidade com o EditorConfig, as configurações do editor de texto são implementadas. Para obter mais informações sobre arquivos EditorConfig, consulte o site [EditorConfig.org](http://editorconfig.org/).

## <a name="override-editorconfig-settings"></a>Substituir as configurações do EditorConfig

Quando você adiciona um arquivo .editorconfig a uma pasta em sua hierarquia de arquivos, as configurações se aplicam a todos os arquivos aplicáveis nesse nível e abaixo. Para substituir as configurações do EditorConfig de um projeto ou base de código específico, de modo que ele use convenções diferentes do que do arquivo de nível superior .EditorConfig, basta adicionar um arquivo .editorconfig à raiz do diretório do projeto ou do repositório da sua base de código. Certifique-se de colocar a propriedade ```root=true``` no arquivo para que o Visual Studio não procure além da estrutura de diretório para arquivos .editorconfig. As novas configurações do arquivo EditorConfig serão aplicadas a arquivos no mesmo nível e aos subdiretórios.

```
# top-most EditorConfig file
root = true
```

![Hierarquia do EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Os arquivos do EditorConfig são lidos de cima para baixo e os arquivos do EditorConfig mais próximos são lidos por último. As convenções de seções do EditorConfig correspondentes são aplicadas na ordem em que foram lidas, portanto as convenções dos arquivos mais próximos têm precedência.

## <a name="supported-settings"></a>Configurações com suporte

O editor do Visual Studio é compatível com o seguinte, do conjunto principal de [propriedades do EditorConfig](http://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- raiz

Há suporte para as configurações de editor do EditorConfig em todas as linguagens compatíveis com o Visual Studio, exceto para XML. Além disso, o EditorConfig dá suporte ao [estilo de código](../ide/editorconfig-code-style-settings-reference.md) e convenções de [nomenclatura](../ide/editorconfig-naming-conventions.md) para C# e Visual Basic.

## <a name="editing-editorconfig-files"></a>Editando arquivos EditorConfig

O Visual Studio oferece IntelliSense para a edição de arquivos .editorconfig. Se você editar vários arquivos .editorconfig, a extensão [Serviço de linguagem do EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) poderá ser útil.

Depois de editar seu arquivo EditorConfig, será necessário recarregar seus arquivos de código para que as novas configurações entrem em vigor.

## <a name="adding-and-removing-editorconfig-files"></a>Adicionando e removendo arquivos EditorConfig

Adicionar um arquivo EditorConfig ao seu projeto ou base de código não converte os estilos existentes em novos. Por exemplo, se você tiver recuos em seu arquivo formatados com tabulações e adicionar um arquivo EditorConfig com recuos com espaços, os caracteres de recuo não serão convertidos em espaços. No entanto, novas linhas de código serão formatadas de acordo com o arquivo EditorConfig.

Se você remover um arquivo EditorConfig do seu projeto ou da base de código, será necessário fechar e reabrir os arquivos de código aberto a serem revertidos para as configurações globais do editor para novas linhas de código.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra o estado de recuo de um trecho de código C# antes e depois de adicionar um arquivo .editorconfig ao projeto. A configuração **Tabulações** na caixa de diálogo **Opções** do editor de texto do Visual Studio foi definida para produzir caracteres de espaço ao pressionar a tecla **Tab**.

![Configuração de tabulação do Editor de texto](../ide/media/vside_editorconfig_tabsetting.png)

Conforme esperado, pressionar a tecla **TAB** na próxima linha faz a linha recuar por meio da adição de quatro caracteres de espaço em branco.

![Codificar antes de usar o EditorConfig](../ide/media/vside_editorconfig_before.png)

Adicionaremos um novo arquivo chamado .editorconfig ao projeto, com o seguinte conteúdo. A configuração `[*.cs]` significa que essa alteração se aplica somente a arquivos de código C# no projeto.

```
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Agora, ao pressionar a tecla **TAB**, você obtém caracteres de tabulação em vez de espaços.

![A tecla Tab adiciona um caractere de tabulação](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Solução de problemas de configurações do EditorConfig

Se houver um arquivo do EditorConfig na estrutura do diretório no local do seu projeto ou acima desse local, o Visual Studio aplicará as configurações do editor nesse arquivo ao seu editor. Nesse caso, você verá a seguinte mensagem na barra de status:

   **"As preferências do usuário para esse tipo de arquivo foram substituídas pelas convenções de codificação desse projeto."**

Isso significa que, se as configurações do editor em **Ferramentas**, **Opções**, **Editor de Texto** (como tamanho e estilo do recuo, tamanho da tabulação ou convenções de codificação) forem especificadas em um arquivo EditorConfig no projeto ou acima dele na estrutura de diretório, as convenções no arquivo EditorConfig substituirão as configurações em Opções. Você pode controlar esse comportamento ativando/desativando a opção **Seguir as convenções de codificação do projeto** em **Ferramentas**, **Opções**, **Editor de Texto**. Desmarcar a opção desliga o suporte do EditorConfig para Visual Studio.

![Opções de ferramentas – seguir as convenções de codificação do projeto](media/coding_conventions_option.png)

É possível encontrar arquivos .editorconfig em diretórios pai abrindo um prompt de comando e executando o seguinte comando na raiz do disco que contém seu projeto:

```
dir .editorconfig /s
```

Você pode controlar o escopo das convenções do EditorConfig configurando a propriedade ```root=true``` no arquivo .editorconfig na raiz do seu repositório ou no diretório em que o projeto reside. O Visual Studio procurará um arquivo chamado .editorconfig no diretório do arquivo aberto e em todos os diretórios pai. A pesquisa termina quando chegar ao caminho do arquivo raiz ou se um arquivo .editorconfig com ```root=true``` for encontrado.

## <a name="see-also"></a>Consulte também

[Convenções de estilo de código do .NET](../ide/editorconfig-code-style-settings-reference.md)  
[Dando suporte ao EditorConfig para um serviço de linguagem](../extensibility/supporting-editorconfig.md)  
[EditorConfig.org](http://editorconfig.org/)  
[Escrevendo código no editor](writing-code-in-the-code-and-text-editor.md)